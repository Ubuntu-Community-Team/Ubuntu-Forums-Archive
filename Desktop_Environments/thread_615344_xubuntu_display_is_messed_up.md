---
title: "xubuntu display is messed up"
date: 2007-11-17
forum: Desktop Environments
---

### Post by miesnerd on 2007-11-17
hey Ive been running ubuntu for a while and since I cant upgrade computers yet (still running with 256M of ram) I thought about switching to XFCE. So naturally i did 
sudo apt-get install xubuntu-deskop
after installing, it asks me if about my default Wm: should it be gdm or xdm?
How do I switch this?
Reason I ask is I tried doing this before and I kept it as gdm for xubuntu, and the screen resolution looked like 300x400 where I couldnt see anything enough to change the display.
So do I need to be using xdm for xfce and gdm for Gnome?
If that's the case, can I set my system up to run xdm with xubuntu and gdm with GNOME?

Thanks.

---

### Post by zhaozhou on 2007-11-17
xdm / gdm does not handle screen size, thats completely up to X itself.
You can set up which one to use with update-rc.d (update-rc.d -h).

xdm / gdm can be thought of as a "logon manager", it lets you log on and select which window manager you want to run.

---

### Post by miesnerd on 2007-11-17
so i guess really I am asking a different question then:
How do I change xubuntu's screenresolution when I cant see much of anything to change it with?
IF i can get a terminal up, then what do I type in to change the resoltion for the way XFCE handles my monitor?

---

### Post by miesnerd on 2007-11-17
update:
I was able to go in and change display settings so that the regular font displayed would be "1" instead of a normal 9 or 12 point font. This made things workable, so now text is readable, but the windows are still huge and clumsy. Does anyone know how to change the display?

---

### Post by zhaozhou on 2007-11-17
If your not to scared of the terminal, i guess you can "sudo nano /etc/X11/xorg.conf", then look for the list of resolutions there.

It should look like '"1024x768" "800x600"' etc etc.

---

### Post by miesnerd on 2007-11-17
I will do that in the terminal.
However, this is exactly why Im positng.
I used the display manager to look at the settings, and it says its displaying the screen size as 1280x1024.
So my thought was that it was something else funky.

---

