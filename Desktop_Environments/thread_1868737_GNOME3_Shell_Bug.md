---
title: "GNOME3 Shell Bug"
date: 2011-10-24
forum: Desktop Environments
---

### Post by GCoffee on 2011-10-24
Hello,

I get this bug on both of my computers (a desktop + laptop). Occasionally when I have multiple applications open (some fullscreen, some not) on multiple workspaces, I go to the activities window to switch between applications, and the full screen application on the other workspace appears behind it (see picture)

[IMG]http://i51.tinypic.com/2hrdaua.png[/IMG]

As you can see from the image, my roundcube webpage (this happens with any application, not just chromium) which is on the workspace below everything else is appearing as a sort of background behind the applications on the current workspace.

Is there any way to easily fix this? Both computers are Ubuntu 11.10 latest updates with GNOME3 installed from the software centre.

(Sorry that some of the image has been blurred out messily)

Thanks,
GC.

---

### Post by crdlb on 2011-10-24
I've seen that too. Apparently, it's a gconf bug somehow:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/844881](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/844881)

It should be fixed in gconf 3.2.1, which isn't available yet.

---

### Post by GCoffee on 2011-10-25
Ok. Thanks :)

---

