---
title: "My install died after update"
date: 2006-06-15
forum: Desktop Environments
---

### Post by frente69 on 2006-06-15
Hi,
Running dapper. 
Came home and there were updates wanting to be downloaded and installed.
After installing the updates and restarting my gui failed to load.
it installed some nvidia update and some image thing and a few others. I don't know,...Being a windows user i only glanced at the updates and clicked install :-)

I only got it up and running yesterday,..
I think it was something to do with the nvidia upgrade where ever it was,. I was able to get the gui back by logging in and running 
"sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf"
found on this guide: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
which i used to setup in the first place. 

Do i really have to rejig the graphics drivers after a nvidia update? How can i fix and try to prevent this from happening in the future,.. i like my gui :-)

---

### Post by Tachyon60 on 2006-06-16
I'm in a freakishly identical situation, after trouble before with ubuntu I finally tried again and got it to work yesterday, but when I updated ubuntu with the ~60 updates that came after 6.06 my gnome desktop won't run correctly, rendering the install basically useless. The login screen was correct, but once I got past that it just sort of sat there and didn't go through the normal startup routine even though there was a working cursor. I was using an ATI radeon 9800 pro so I'm not sure it's video card related, although I was using dual screen.

---

### Post by frente69 on 2006-06-16
Try this it fixed my problem less then 5 mins ago :-) :
[http://www.ubuntuforums.org/showpost.php?p=1143860&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1143860&postcount=9)

[edit]I just noticed that you are running ATI so it isn't relevent to you,...does ATI make a similarly installing driver? From what i hear their GPU support is pretty crummy for nix?

I found that even tho i had the linux-386 package thing installed to get the drivers working initially,..after the update they magically went missing,... weird!

---

### Post by Tachyon60 on 2006-06-16
I honestly couldn't tell if you they went missing or not, but because gnome partially works instead of being completely broken, I don't really think it's a gpu thing, although since I have very little idea what I'm doing in linux I could be wrong. I just reinstalled ubuntu since I haven't done anything too complicated so far. Thanks for posting your fix though!

---

### Post by leech on 2006-06-16
Actually on my end it had nothing to do with the nvidia drivers, it was because of the Wacom stuff in xorg.conf that it was screwing up on my laptop.  

Leech

---

### Post by longinus on 2006-06-16
I couldn't boot into X too, after upgrading.

What I found out later (after changing the driver to 'nv' to get to gnome) was that the package "linux-restricted-modules-2.6.15.25" didn't install/upgrade. I was still with the 2.6.15.23... So the kernel stuff for the 'nvidia' couldn't load..

I installed the package and it worked.

---

### Post by tseliot on 2006-06-16
There is a part of my guide titled "WHAT HAPPENS IF YOU CHANGE YOUR KERNEL OR IF YOUR KERNEL IS UPDATED" and yes, it's so big that you can't miss it:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

