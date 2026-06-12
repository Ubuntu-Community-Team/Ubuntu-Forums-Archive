---
title: "Computer was haunted. Found out why. How to fix please"
date: 2009-01-25
forum: General Help
---

### Post by Fred Doolie on 2009-01-25
Hi,


For a while I thought my computer, a Mega-180, was haunted. I would get random numbers in text boxes, the volume control would show and move up or down and worst of all the shutdown dialog would pop up. This only happened under Ubuntu; never Windows. I thought the system was shorting out or something. Well, just now I found the problem. The remote control for my TIVO is doing it! The buttons on the remote cause Ubuntu to do weird stuff.

I had forgotten that the Mega-180 could be controlled with an IF remote. I've never used the remote or the multimedia software that came with the computer. It looks like Ubuntu sees the IR sensor in the computer and thinks I have a wireless keyboard controller. Wow. Maybe it knows the computer is a remote-controlled media machine. Even so I don't want the IR port active since my TIVO is in the computer room.

How do I find and disable the IR driver?

   
Thanks

---

### Post by theozzlives on 2009-01-25
My guess would be in the CMOS Setup,

---

### Post by Fred Doolie on 2009-01-25
I can't find anything like that in the Ubuntu menus. Doesn't Ubuntu have a place to see what drivers are loaded and change/update/disable them? In Winblows it's in the Control Panel.

---

### Post by Dr Small on 2009-01-25
> **Fred Doolie said:**
> I can't find anything like that in the Ubuntu menus. Doesn't Ubuntu have a place to see what drivers are loaded and change/update/disable them? In Winblows it's in the Control Panel.
The CMOS settings is the BIOS settings for your motherboard. Find out what key opens the BIOS settings on your system and look around in the settings.

---

### Post by rattking on 2009-01-25
hi
I think the lirc driver handles remote control interfaces 
in a terminal
lsmod | grep lirc
will tell you what lirc drivers are loaded
then you can put that driver name in

/etc/modprobe.d/blacklist

and ubuntu wont load that driver next boot
hope that helps

---

