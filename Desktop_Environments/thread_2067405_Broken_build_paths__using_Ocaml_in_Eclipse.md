---
title: "Broken build paths :/: using Ocaml in Eclipse"
date: 2012-10-06
forum: Desktop Environments
---

### Post by cavetrolldigger on 2012-10-06
Helo, yesterday I've deleted few library (lexer, parser /.ml/.mli/.cmi,..) files in /usr/lib/ocaml/stdlib by mistake, so I couldn't use them in Ocaml. When I figured it out I've decided to switch default package 3.12 to 4.0. I uninstalled ocaml with apt-get (unfortunately, later, I wrote also rm * in /usr/lib/ocaml), downloaded sources for 4.0 compiled and installed new one. Now [which ocaml] shows that it is under /usr/local/bin/ocaml (previously was /usr/bin/ocaml).

That was what I did. I can write, compile, use stdlib in top-level ocaml (open Pervasives;;) via console (even inside eclipse toplevel console). But after reinstallation, eclipse can't compile modules anymore. It gives me error:

[HTML]Errors occurred during the build.
Errors running builder 'Ocaml Builder' on project 'lab1'.
Path must include project and resource name: /:[/HTML]I'm using OcalIde plugin. I though that library paths has changed so I've replaced /usr/bin/ocaml with /usr/local/bin/ocaml etc. in properties->paths. [paths_screenshot]("http://imageshack.us/a/img233/1672/29259120.png") I've replaced eclipse with new one and installed plugin again and still, I get the same error.

I've tried to force reinstallation of default ocaml package via apt-get and dpkg, but it doesn't work, even with --force-download it doesn't get library files to /usr/lib/ocaml. But tbh 4.0 works just fine, except taht OcamlBuilder in eclipse.

Obviously, before I deleted those library files,everything worked jut fine

Can you help me please?

---

### Post by cavetrolldigger on 2012-10-08
Solved by reinstalling all default packages

---

