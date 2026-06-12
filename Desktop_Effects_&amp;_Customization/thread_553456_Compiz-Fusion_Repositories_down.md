---
title: "Compiz-Fusion Repositories down?"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by DaH-RaT on 2007-09-17
hi, just wondering if the compiz-fusion and/or beryl packages were down for download?
if not for some reason i cannot  install them aka terminal or Synpatics. plus does compiz-fusion have a GPG key? thats the only process of elemination i could not do due to not finding one.

Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

---

### Post by mcgarry83 on 2007-09-17
Im having a similar problem. I did my updates today but some of them just wouldn't go through. They were all compiz packages. Not sure whats going on, but I heard there were a bunch of problems with the new updates breaking stuff. Maybe they pulled them down to figure out what went wrong. When I try to update it tells me I must do a partial upgrade because some packages would not. Then when I click partial, I get this...

Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
compiz
compiz-core
compiz-gnome
compiz-plugins
libfuse2

---

### Post by Caffeine_Junky on 2007-09-17
> **mcgarry83 said:**
>   .......Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
compiz
compiz-core
compiz-gnome
compiz-plugins
libfuse2

yeah,  same here.   don't sweat-it, all will be sorted soon I should imagine :popcorn:

---

### Post by DaH-RaT on 2007-09-18
yea its fixed now i think :) thanks

nope not fixed noticed its probably a huge network issue seeing as almost all the synaptics is having host connection problems.

---

### Post by hyperair on 2007-09-18
DId you remember to add the GPG key? I don't have the problem =\ Anyway you can install without authenticating can't you?

---

### Post by DaH-RaT on 2007-09-18
not exactly sure but i installed beryl, it gave  http errors while installing beryl but still isntalled and works fine. im getting gpg errors for everything i download now, Via synaptics and terminal. im guessing its a network problem , either me or the mains

---

### Post by hyperair on 2007-09-18
Probably you. I don't have any problem.

---

### Post by Rupertronco on 2007-09-18
> **hyperair said:**
> Probably you. I don't have any problem.

You're just full of help.

---

### Post by hyperair on 2007-09-19
[quote=Rupertronco]
You're just full of help.
[/quote]
Thanks. I know I am.

---

### Post by DaH-RaT on 2007-09-19
well anyway, does someone actually KNOW why?

lee@lee-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
lee@lee-desktop:~$ sudo dpkg --configure -a
Password:
Setting up msttcorefonts (1.8ubuntu1) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on msttcorefonts; however:
  Package msttcorefonts is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 msttcorefonts
 ubuntu-restricted-extras
lee@lee-desktop:~$

---

