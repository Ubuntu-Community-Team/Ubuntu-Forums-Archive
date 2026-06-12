---
title: "Environment variables not set in Emacs launched from Gnome Panel"
date: 2010-11-03
forum: Desktop Environments
---

### Post by clconway on 2010-11-03
My .bash_env file set several environment variables, including PATH and EMAIL, but in an Emacs session launched from the Gnome Panel (command: "/usr/bin/emacs23 %F") these variables do not have the expected values. I've run into this problem before (see [this blog post]("http://procrastiblog.com/2007/07/09/changing-your-path-in-emacs-compilation-mode/")). I fixed it then by sourcing .bash_env in my .xsession file. Obviously, this is no longer working. 

The variables are set properly if I manually launch Emacs from a termainl. Oddly, they aren't set if I change the panel launcher to execute Emacs in a terminal (I would think this would start Bash before starting Emacs).

Any ideas?

---

