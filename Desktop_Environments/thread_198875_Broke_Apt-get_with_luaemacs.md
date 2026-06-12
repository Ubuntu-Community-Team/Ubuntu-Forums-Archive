---
title: "Broke Apt-get with lua/emacs"
date: 2006-06-17
forum: Desktop Environments
---

### Post by Sharkee on 2006-06-17
I got Wargus (a Warcraft 2 knockoff) from a site and was attempting to install it .  I didn't realize for a sec I only had the source code (indicated by the makefile and build.sh).

It gave some error and said it needed lua-mode or something, so I apt-got it, now I can't seem to install anything w/o getting apt-get/lua/emacs errors.

Here's an example of me trying to install the package "gpsdrive"
```

*[INDENT] sudo apt-get install gpsdrive[/INDENT]*
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  gpsd
The following NEW packages will be installed:
  gpsdrive
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/1280kB of archives.
After unpacking 2396kB of additional disk space will be used.
Selecting previously deselected package gpsdrive.
(Reading database ... 118520 files and directories currently installed.)
Unpacking gpsdrive (from .../gpsdrive_2.09-2ubuntu1_i386.deb) ...
Setting up emacs21 (21.4a-3ubuntu2) ...
emacs-install emacs21
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/flyspell.elc
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/lua-mode: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/lua-mode/lua-mode.el:
  !! Symbol's value as variable is void ((lua-left-shift-regexp-1))
Done
emacs-install: /usr/lib/emacsen-common/packages/install/lua-mode emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 3.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lua-mode:
 lua-mode depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing lua-mode (--configure):
 dependency problems - leaving unconfigured
Setting up gpsdrive (2.09-2ubuntu1) ...

Errors were encountered while processing:
 emacs21
 lua-mode
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I currently have the following packages installed (at least these):
```
lua40   lua50   lua-mode   liblua*
emacs21 emacs21-bin-common   emacs21-common
```

[B]How can I fix what I've done?
How do I install Wargus,  or any program that I DL the source from?[/B]

I didn't know what I was doing.  I thought I could figure it out since I'm really good w/ Windows.  I guess that's a motif around here though.  

Your help and expertise is greatly apppreciated.

---

### Post by Sharkee on 2006-06-23
Can someone please help me with this?  I'm stuck and can't install updates, or remove anything!

---

