---
title: "compiz: couldn't load plugin 'keybindings'"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by Rapax on 2007-09-22
Hi guys

I'm having some trouble getting compiz fusion to work on my machine.
I have installed the latest Nvidia drivers for my 8600GT using envy (100.14.19, right?)
Hardware acceleration seems to be working fine, glxgears shows roughy 11600 frames per seconds.
I've installed compiz fusion as described here: 
[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)
and I didn't get any errors or warnings during installation.

When I run 'compiz --replace' from the command line, I get the error message:
"compiz: couldn't load plugin 'keybindings'"

CF does seem to start, and the desktop reappears after a second or two, but it is extremely sluggish (to the point of freezing for several minutes during simple stuff like moving a window, and the error message keeps repeating. I usually have to Ctrl-Alt-Backspace to get out of it.

Specs: Ubuntu feisty, running on AMD64, with an Nvidia 8600GT

Any ideas?

---

### Post by Rapax on 2007-09-23
I was thinking the solution would probably be to re-install the 'keybindings' plugin, but it doesn't seem to be available alone. All the pages and lists of plugins I've found are "extra" ones. How can I reinstall a basic plugin in CF?

---

### Post by Forlong on 2007-09-23
You are using bleeding edgy packages for Compiz that are known to break sometimes.
I recommend using Amaranth's backported packages.

You can use my How-To if you like - see [this thread]("http://ubuntuforums.org/showthread.php?t=536149").

---

