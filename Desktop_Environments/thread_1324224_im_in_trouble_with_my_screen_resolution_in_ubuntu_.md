---
title: "im in trouble with my screen resolution in ubuntu 9.10 desktop. please help soon"
date: 2009-11-12
forum: Desktop Environments
---

### Post by MrLOVER on 2009-11-12
hi, im a new user of linux, i installed ubuntu 9.10 desktop edition 2 days ago and everything was fine, today i don't know what happened when i started my machine its screen resolution is very low that i can't even see full windows. i can't see a small dialog box completely into my display area. everything is so big and out of screen. i don't know how to solve it. i searched everywhere but couldn't get answer to my problem.
please tell me how i can reset my display resolution to default from grub menu consol.

Note! i didn't changed any hardware or didn't updated my windows. last thing i did to it was i was trying to install dnsmasq and ipmasq.

please i need urgent reply. i don't wanna re-install my ubuntu :(

---

### Post by oktay_y2003 on 2009-11-12
Is it possible to change resolution from Display setting? what do you see there?

---

### Post by wojox on 2009-11-12
You need to drop into a root shell not a grub menu.

nano /etc/X11/xorg.conf

Look for Section "Screen" and change the option to 1028x1024

---

### Post by MrLOVER on 2009-11-12
thanks you everyone for your help, but i was not able to see any thing on my desktop due to everything was too big, my resolution was some 300x200 around about and my monitor is 19 inch.

but after searching a lot i found what i wanted. so im sharing with you here so that other new users like me can also know this.
if incase you set your resolution to very low and or any kind of resolution trouble. you can use the following command in your terminal or grub terminal to reset your resolution to your choice.

**[COLOR=DarkRed]$ xrandr --output default --mode 1024x768 --rate 75[/COLOR]**

here --mode is your screen resolution and --rate is your refresh rate,

thanks :)

---

### Post by wojox on 2009-11-12
Oops the old X Resize and Rotate Extension. Good job.

---

### Post by LeeM on 2009-11-13
I also have a resolution problem when I upgraded to Karmic. It set my screen resolution to 800x600, where the screen should be 1280x800. I tried the following:
Detect monitor - nothing 
Previous help suggested editing /etc/X11/xorg.conf - That file isn't present in /etc/X11 !!
use command line to change via xrandr (earlier in this thread) - the response said that 800x600 was the max available resolution.

Any ideas what to try now??

Thanks!

---

### Post by LeeM on 2009-11-13
OK,  finally solved my own problem :D 
I just grabbed the xorg.conf from the backup of /etc/X11 before upgrading, and plopped it into the new /etc/X11. Works after a re-login!

(Still don't know why there wasn't an xorg.conf in Karmic??)

---

