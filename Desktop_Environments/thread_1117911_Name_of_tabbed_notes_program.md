---
title: "Name of tabbed notes program?"
date: 2009-04-06
forum: Desktop Environments
---

### Post by litlfrog on 2009-04-06
I used to work on an xubuntu machine that had this notes program I really loved. It came up as one window with tabs along the left side for you to create new notes. It's the best quick notes application for my workflow, but now I'm on an Ubuntu machine and I can't remember the name of it! I'd think that it could run fine on Ubuntu with a quick command-line install. Can anyone give me the name of that program please?

---

### Post by alfplayer on 2009-04-06
You can search for it and install it with Synaptic: *System -> Administration -> Synaptic Package Manager*

---

### Post by litlfrog on 2009-04-06
OK, good to know that it's readily available through Synaptic, but does anyone know the name of the package?

---

### Post by alfplayer on 2009-04-06
No, I meant that if you didn't use it a long time ago it's probably in recent versions of Ubuntu.
Using Synaptic you can search for packages that have the word "note" or "notes" as part of their names or descriptions, so you may recognize the name of the program you used in the search results or try others.

---

### Post by litlfrog on 2009-04-07
Okay, I've confirmed that the program is the xfce4-notes-plugin that comes with xubuntu. Is there a way to launch that program in Gnome? Just trying to launch it from the terminal doesn't do anything.

---

### Post by Therion on 2009-04-07
If you can't download the applications package(s) from Synaptic then you will need to install the Xfce desktop (not USE it, mind you, but have it installed) in order to get access to the application.  I did find links to source files if that helps:

[http://goodies.xfce.org/projects/panel-plugins/xfce4-notes-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-notes-plugin)

[http://goodies.xfce.org/releases/xfce4-notes-plugin/](http://goodies.xfce.org/releases/xfce4-notes-plugin/)

---

### Post by litlfrog on 2009-04-07
xfce has been installed right along. The package is already listed as installed in Synaptic; the package name is xfce4-notes-plugin. I reinstalled it just to be sure.

> joey@xubuntu1:~$ xfce4-notes-plugin
bash: xfce4-notes-plugin: command not found


That's what I get when I try to run the command. Is there a different way I should be starting this?

---

### Post by alfplayer on 2009-04-07
I think you don't need to have the entire Xfce desktop installed. Maybe you find this is useful: [http://ubuntuforums.org/showthread.php?t=680618](http://ubuntuforums.org/showthread.php?t=680618)

---

### Post by Therion on 2009-04-07
> **litlfrog said:**
> That's what I get when I try to run the command. Is there a different way I should be starting this?
Try "xfce-notes" instead?

---

