# The CLI

To install the __elm-spa__ CLI via [npm](https://npmjs.org) run this command:

```terminal
npm install -g elm-spa@latest
```

This CLI gives us these six commands:

1. [__elm-spa new__](#elm-spa-new) - creates a new project
1. [__elm-spa server__](#elm-spa-server) - runs a dev server as you code
1. [__elm-spa add__](#elm-spa-add) - adds a page to an existing project
1. [__elm-spa build__](#elm-spa-build) - one-time production build
1. [__elm-spa gen__](#elm-spa-gen) - generates files, without elm make
1. [__elm-spa watch__](#elm-spa-watch) - generates files as you code

What do these do? Let's dive into each in detail!

## elm-spa new

When you want to create a new project, use the `elm-spa new` command. This creates a new project in the current folder:

```terminal
elm-spa new
```

```bash
New project created in:
/Users/ryan/code/my-new-app
```

The `new` command creates __three__ files:

Filename | Description
--- | ---
`elm.json` | Keeps track of [Elm packages](https://package.elm-lang.org).
`src/Pages/Home_.elm` | The project's homepage.
`public/index.html` | The HTML entrypoint to the app.

## elm-spa server

The first thing you'll want to do after creating a new project is see it in the browser! The `elm-spa server` command is all you need to see the app in action:

```terminal
elm-spa server
```

This command starts a development server for your project at [http://localhost:1234](http://localhost:1234).

> When you edit your code, `elm-spa server` automatically compiles your application.


## elm-spa add

You can add new pages to your app with the `elm-spa add` command:

```terminal
elm-spa add /contact
```

This creates a new file at `src/Pages/Contact.elm`. If you visit [http://localhost:1234/contact](http://localhost:1234/contact) in the browser, you'll see a new page with the text `"Contact"` displayed.

### adding other pages

Here are a few examples of other routes you can create with the add command

```bash
elm-spa add /              # src/Pages/Home_.elm
elm-spa add /settings      # src/Pages/Settings.elm
elm-spa add /people/:id    # src/Pages/People/Id_.elm
```

We'll cover this in more detail in the [routing section](./02-routing)

### using page templates

The `elm-spa add` command also accepts an optional `template` argument too for common pages you might create.

```bash
elm-spa add /example static
elm-spa add /example sandbox
elm-spa add /example element
```

We'll explore those page types in the [pages section](./03-pages)

## elm-spa build

The `elm-spa server` command is great for development, but for __production__, you'll want the `elm-spa build` command.

```terminal
elm-spa build
```

This compiles your app into __an optimized and minified JS file__. This makes it great for serving your application in the real world!

### A note on hosting

By default, the `public` folder can be statically served. Hosting platforms like [Netlify](https://netlify.com) make this free and easy.

Because this is a single page application, be sure to setup redirects to `public/index.html`. Here's an [example of how to do this with Netlify](https://docs.netlify.com/routing/redirects/rewrites-proxies/#history-pushstate-and-single-page-apps).

## elm-spa gen

If you are working with another dev server, you won't need the `.js` file generated by the `build` command. To only generate __elm-spa__ files, use the `elm-spa gen` command:

```terminal
elm-spa gen
```

This will generate code in the `.elm-spa` folder, but allow your custom workflow to define it's own way of compiling Elm. This is a great command to combine __elm-spa__ with another tool like [Vite](https://vitejs.dev) or [Parcel](https://parceljs.org/elm.html).


## elm-spa watch

If you want the automatic code generation on change, but don't need elm make or an HTTP server, you can use the `elm-spa watch` command:

```terminal
elm-spa watch
```

This will automatically generate code and compile your Elm files on save, but without the server.

---

__Next up__: [Routing](./02-routing)
