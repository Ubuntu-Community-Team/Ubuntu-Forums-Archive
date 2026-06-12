---
title: "Changing icons not always possible"
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by tomaasj on 2007-07-09
Anyone,

I am changing my desktop etc. and it seems to go forward somehow.  I noticed that I am not always able to change application icons.  For example, the app Streamtuner has a green triangle for an icon which I would like to change.  In the folder where it resides (if I recall correctly:  usr/share/applications), the computer tells me I have no permission etc. to change its appearance.  I made Streamtuner to appear as a launcher on the desktop and change the icon on that level, but I noticed that it does not remain so when restarting the computer. I did the same with the Firefox icon, but that one somehow appears to keep its altered icon, which momentarily resides in a dock on my desktop.

Can someone elaborate on this.  If relevant, is it possible to change the icons of apps in usr/share/applications ?

Tomaasj

---

### Post by prince_niceguy on 2007-07-09
if you have installed the icons yourself i.e. not built in default it would be under <your home dir>/.icons. you can change the image there and it should work.

---

### Post by tomaasj on 2007-07-10
Hi,

what I tried to do is go to the usr/share/applications folder, right click on the icon of the application which I wanted to change, navigate to the folder you mentioned where I installed some icons and paste one of them.  This does not work.  It says I do not have permission etc.  How to solve ?

Tomaasj

---

### Post by prince_niceguy on 2007-07-11
which icons are you trying to install? can you provide a ls -l in the /usr/share/application directory. might be some permissions issue.

---

### Post by tomaasj on 2007-07-11
this is what I found when navigating via terminal to the application which icon I would like to change:

-rw-r--r-- 1 root root   642 2007-01-12 19:05 streamtuner.desktop

---

