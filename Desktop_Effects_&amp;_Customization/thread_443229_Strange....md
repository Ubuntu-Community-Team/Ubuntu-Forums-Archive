---
title: "Strange..."
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by wwoollff on 2007-05-14
I have used Beryl several times, and it worked fine every time.But now, I have a major problem. I have upgraded my Edgy (with Beryl) to Feisty, reinstalled the Nvidia driver (/etc/X11/xorg.conf contains the name of my monitor, video card, everthing is fine), reinstalled beryl, but when I try to launch it, I get the icon in the right side of the screen, but the screen doesn't change at all.I have selected Beryl as the Window Manager,tried to change the emerald themes, but nothing worked.And, the strangest thing is that I have only General Options in Beryl Setting Manager.Is there any way to fix this?

thx alot.

---

### Post by Death_Sargent on 2007-05-14
first of all be sure you did every thing in the beryl wiki fiesty install guide as it is much different than the edgy install guide and you have to do a few extra things 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia")

this  means do a comlete uninstall.

Also be sure to reinstall emerald as it gets seriously screwed up during the upgrade.

The reason for the old way of installing beryl not working is because your distro is set to prefer compiz by default. this makes beryl unuzable. simply make sure to use synaptic to purge your system of any beryl apps and then to reinstall from scratch.

---

### Post by wwoollff on 2007-05-14
thx. Everything works fine.I've forgot to remove also all the libraries and they were blocking everthing. thx alot again.

---

