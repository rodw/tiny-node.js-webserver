# a tiny node.js webserver

## What is it?

The tiny node.js webserver (hereafter, "tnws") is just that, a simple webserver implemented as a single, stand-alone CoffeeScript (or JavaScript) file.

By design, the tnws has **no external dependencies** outside of the core node.js libaries (and CoffeeScript, unless you're working with the "compiled" JS file).

There are [many other](https://github.com/joyent/node/wiki/modules#wiki-web-frameworks-static) simple node.js applications for serving static files over HTTP, however the tnws is the only one I know of meets the "all-in-one-file" criterion.

## Why is it?

Sometimes you just need a little webserver.  

Specifically, web browsers often treat resources served from local `file://` URLs slightly differently those via `http://` URLs.  The tnws offers a quick-and-dirty way to serve local files over HTTP, which can come in handy when developing web applications based on local HTTP/JS/CSS files, etc.

## How do I use it?

Just fetch the `tnws.coffee` file:

    curl -O https://raw.github.com/rodw/tiny-node.js-webserver/master/tnws.coffee

(or otherwise download the file at [this url](https://raw.github.com/rodw/tiny-node.js-webserver/master/tnws.coffee)).

And run it:

    coffee tnws.coffee

or simply:

    ./tnws.coffee

That's all.  The tnws should now be listening at port 8080 on your localhost.  For example, you can fetch the `twns.coffee` source code itself by visiting <http://localhost:8080/tnws.coffee>.

### Installing TNWS in Your Path

If you use the tiny node.js webserver often, you may want to install it somewhere in your `$PATH`.

For instance, if the directory `~/bin` exists and is in your path, then you can save `tnws.coffee` into that directory:

    curl -o "~/bin/tnws" https://raw.github.com/rodw/tiny-node.js-webserver/master/tnws.coffee

and thereafter, launch a web server instance serving files from the current directory with just `tnws`.

### Options

The tnws can be configured through a few simple command-line arguments.

In full:

    tnws --port <port> --host <host> --docroot <docroot> \
         --index <filename> --mime-type <ext> <value> \
         --quiet --silent

where:

 * `--host` or `-h` specifies the hostname to bind to (defaults to `127.0.0.1`).
 * `--port` or `-p` specifies the port to listen on (defaults to `8080`).
 * `--docroot` or `-d` specifies the directory from which to serve files (defaults to `.`).
 * `--index` or `-i` specifies the file to serve when a directory is requested (defaults to `index.html`).
 * `--mime-type` or `-m` specifies that files with the extension `<ext>` should be served with the MIME type `<value>`. Note that you can repeat the `--mime-type` flag to specify multiple mappings.
 * `--quiet` or `-q` supresses the `<STATUS-CODE> <REQUEST-METHOD> <REQUEST-URI>` log messages that tnws otherwise generates for every request serviced.
 * `--silent` or `-s` supresses all non-error console messages. (Note that `--silent` implies `--quiet`.)

These arguments are all optional.

## Licensing 

The tnws is distributed under the [MIT License](http://www.opensource.org/licenses/mit-license.php), as specified in [`LICENSE.txt`](./LICENSE.txt) and in the [`twns.coffee`](./LICENSE.txt) file itself.
