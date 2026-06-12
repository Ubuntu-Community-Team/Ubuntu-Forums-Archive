---
title: "Installing Akamaru error"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by Leela on 2007-06-26
I'm trying to install this dock called Akamaru, and I'm following everything what's here:
[http://www.macewan.org/2006/07/23/howto-install-akamaru-dock-on-ubuntu/](http://www.macewan.org/2006/07/23/howto-install-akamaru-dock-on-ubuntu/)
the problem is, when i do this
```
git clone http://people.freedesktop.org/~krh/akamaru.git
```
I get this:
```
root@leela-desktop:~# git clone http://people.freedesktop.org/~krh/akamaru.git

git, the filemanager with GNU Interactive Tools, is now called gitfm.

If you are looking for git, Linus Torvald's content tracker, install
the cogito and git-core packages and see README.Debian and git(7).

This transition script will be removed in the debian stable
release after etch.

If you wish to complete the transition early, install git-core
and use (as root):
 update-alternatives --config git

Press RETURN to run gitfm


GNU Interactive Tools 4.3.20 (i686-pc-linux-gnu), 16:31:59 Nov  9 2006
GIT is free software; you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software
Foundation; either version 2, or (at your option) any later version.
Copyright (C) 1993-1999 Free Software Foundation, Inc.
Written by Tudor Hulubei and Andrei Pitis, Bucharest, Romania

**/usr/bin/gitfm: fatal error: `chdir' failed: permission denied.**

```
Anyone knows how to fix this?

Thanks

---

### Post by PaulFr on 2007-06-26
Please run ```
sudo apt-get install cogito git-core curl
``` in a terminal to install git and curl.

---

### Post by Leela on 2007-06-26
Did that, when i did ```
git clone http://people.freedesktop.org/~krh/akamaru.git
``` I had same error

---

### Post by Leela on 2007-06-26
anyone...?

---

### Post by PaulFr on 2007-06-26
Please run **sudo update-alternatives --config git** as instructed in the message that comes when you run git : This will put up two options, one indicating git-scm and the other indicating git-transition. Please select the number corresponding to git-scm. Then, the command 'git' will refer to the git tool and not to the gitfm tool.

---

