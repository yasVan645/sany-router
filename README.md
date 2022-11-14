# San Router 1.0.0
A simple Javascript router library for Single-Page Application (SPA)s.

Demo page : <a href="https://yasvan645.github.io/san-router-demo/#/" target="_blank">[ HERE ]</a>

# Installation

<code> npm i san-router</code>
<br>
<hr>

# Usage

- Using import. [ Importing directly from nodemodule folder ]
```

import sanRouter from './node_modules/san-router.js'

```

- Import your pages, in this case we hav three pages [ home.js, about.js, projects.js ]
```

import home from './pages/home.js';
import about from './pages/about.js';
import projects from './pages/projects.js';

```
<hr>

### Pages [ This is how your pages might look ]

- home.js
```
const home = {
    render: async () => {
        let view = `
            <p>👋Home page🎊</p>
        `
        return view;
    },
    after_render: async () => {
        console.log('This is home page');
    }
}
export default home;
```

- about.js
```
const about = {
    render: async () => {
        let view = `
            <p>About page</p>
        `
        return view;
    },
    after_render: async () => {
        console.log('This is about page');
    }
}
export default about;

```

- projects.js
```
const projects = {
    render: async () => {
        let view = `
            <p>Projects page</p>
        `
        return view;
    },
    after_render: async () => {
        console.log('This is projects page');
    }
}
export default projects;

```
<hr>

- Initialize router callback
```

const router = new sanRouter({
  mode: 'hash',   //sets listening mode to hash. altenates -> ['hash','href']
  root: '/',    //sets the current directory to '/'
});

```
- Define main container element.
```

const root = document.getElementById('root');

``` 

- Add hash callback functions.
```
router
.add(/about/, async () => {  //Fires when the current hash = 'page.com/#/about'
  root.innerHtml = await about.render();
  await about.after_render() 
})
.add(/projects/, async () => {  //Fires when the current hash = 'page.com/#/projects'
  root.innerHtml = await projects.render();
  await projects.after_render() 
})
.add('', async () => {  //Fires when the current hash = 'page.com/#/' or any hash with doesn't match the the given hashes.
  root.innerHtml = await home.render();
  await home.after_render() 
})

```
<hr>

# Conclusion
San Router is a very basic and easy-to-use js library for anyone struggling with single-page routing.

Hope you found that usefull, do not forget to give the repo a star 🤩.

# 🪲 For any issues

[BUGS](https://github.com/yasVan645/san-router/issues) <br>
[HOMEPAGE](https://github.com/yasVan645/san-router#readme)

# Made with 😍 and 🍵 by [yasvan](https://github.com/yasVan645)