---
title: "Issue after installing Beryl+XGL- might be user error"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by danayanch on 2007-05-11
Hi All,

I am new at Linux/Ubuntu Feisty Fawn, but after installing a fresh copy I can't get enough of it. After viewing a video of Beryl etc on youtube I decided to try and install it.

I followed this guide: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

I installed it with success and all the effects run surprisingly well on my notebook.

Here are my problems:

1. My shutdown button has disappeared. 

2. I cannot seem to get the emerald themes working properly. As you can see in this photo: [http://img292.imageshack.us/img292/8458/screenshot1xy0.png](http://img292.imageshack.us/img292/8458/screenshot1xy0.png)

I can get the _ [] X buttons in the top right corner to look fine, but the title bar etc don't seem to load. 

I am not sure but, in the tutorial it said that i should see a beryl splash screen when it starts up, but i never see a splash screen.  Despite this, beryl seems to be running and the effects work (zoom out selection thing, cube, etc)

Anyone have any ideas? I am still searching through all these posts, but cannot find solutions.

Thanks all!


Oh I should add this is my setup:

Ubuntu Feisty Fawn (32bit)
Compaq V2450CA Notebook
ATI XPRESS 200M
Amd Turion 64 1.6 GHz
1GB Ram

Dana Y.

---

### Post by danayanch on 2007-05-11
Hi All,

Ok I solved the issue with the themes, so no worries there! :D!!! Looks so hawt.

I also found this for the shutdown issue, but don't understand what the user means, or what to do with the info:

Nice guide, I followed this guide a few months ago and it makes beryl running on my thinkpad T60, although one small issue is that in the XGL session, you don't have the option of "restart" or "shutdown" when you click the logout button, so I either need to logout or use "sudo shutdown -r now" in order to shutdown my laptop.
Today I found from the beryl forum that if you use the following /etc/bin/startxgl script, you can solve the problem:
------------------------------------

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

---

### Post by danayanch on 2007-05-11
Ok, I figured out all my problems. I just added that script to the startxgl file and it works now.

yayyy.

---

