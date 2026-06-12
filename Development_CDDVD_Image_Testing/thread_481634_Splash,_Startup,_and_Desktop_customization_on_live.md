---
title: "Splash, Startup, and Desktop customization on live cd"
date: 2007-06-22
forum: Development CD/DVD Image Testing
---

### Post by inanutshellus on 2007-06-22
So I'm setting up a custom live cd and trying to set up a custom wallpaper and boot screen. I read somewhere the boot screen was the "/isolinux/splash.pcx" file on the CD and sure enough, it fit the bill. I modified the image and saved it to the same place. 

I also followed the ubuntu wiki instructions ([https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)) on setting up a different default desktop:

> Custom Background for GNOME

Generally background files are located in /usr/share/backgrounds. Edit the file /var/lib/gconf/debian.defaults/%gconf-tree.xml and change the string /usr/share/backgrounds/warty-final-ubuntu.png to point to your file.


For some reason neither of these took hold. What's the deal?

---

### Post by inanutshellus on 2007-06-25
Arg, /etc/profile isn't loaded either...

---

### Post by inanutshellus on 2007-07-09
I ended up using Reconstructor to get the splashes working but I never did figure out how to get my environment variables read on boot. I ended up changing the shortcuts of the apps that needed them to instead of just exec the app, to first source the /etc/profile then run the app. In other words, I made a shortcut, then edited it in a text editor and changed the line that said "Exec" from:

Exec: *myappp*

to

Exec: source /etc/profile; *myappp*

Lame, but... it works.

---

