---
title: "how to have 256 bit gnome session (RDP) ?"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by sampei7777 on 2007-11-28
Hi all

I installed Ubuntu 7.10 on a VMware virtual machine

I also installed the xrdp package from [http://xrdp.sourceforge.net/](http://xrdp.sourceforge.net/)

So now I am able to connect to the Ubuntu machine from both windows and linux PC using RDP clients (such as rdesktop for linux and microsoft client terminal services for windows)

The problem is that some my RDP clients only support 256 color (8 bit depth resolution).

When I connect from these clients I can only see the wallpaper of the gnome session, while other things (such as panel applets) blink and then disappear.

The problem is related to 8 bit depth and gnome session because if I launch rdesktop with -a8 option I have the same behaviour.

On the other hand if I do not launch gnome-session but xterm it works on these 256 colors RDP clients.

So, how to have a gnome-session that works with 256 colors?

I tried to set up websafe colors following this document:
[http://www.gnome.org/learn/admin-guide/latest/performance-8.html#performance-3](http://www.gnome.org/learn/admin-guide/latest/performance-8.html#performance-3)

I also tried to edit /etc/X11/xorg.conf file by adding 
DefaultDepth 8
in the "Screen" section

I also tried to replace xorg.conf file with the xorg.conf file before VMware tools installation.

Finally, I tried to do
sudo apt-get install nvidia-glx
and
sudo nvidia-xconfig
(even if I have a VMware SVGA...)

All these things did not work.

Thanks in advantage.

PS: in the subject I did a mistake. It is 256 colors, not bit

---

