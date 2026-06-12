---
title: "Xorg Interface error"
date: 2006-01-10
forum: General Help
---

### Post by mofomikeman on 2006-01-10
I have an nVidia GeForce FX 5500. I need to (i think) dissable my Intel built-in graphics card. In the BIOS I looked at every option. I updated to the news BIOS variation. Still no dice. The option for video card has built-in or Auto. Since my built-in is still active, linux recognizes it instead. I did the sudo dpkg-reconfigure xserver-xorg, and set it all up. I put nv for the driver (it looked like nvidia, closest thing on there, they were just like two letter things and such.), but it still weant for the built-in. I wasn't sure what to put for the PCI slot thing, so I left it alone. I think that MIGHT be it, but more than one person has said if I disable the built-in through my BIOS (which, I told you, it isnt in the dell one) it will auto detect the slot. Can I use like an open source BIOS? Help.

Currently booted into Windows XP Home Edition

---

### Post by Ocxic on 2006-01-10
choose auto for you vid card option, usually if there is a video card in the motherboard, the on board video gets disabled. if xorg still uses you on board video, install ubuntu, and when you get to the login prompt, login and type

lspci   - this will give you a listing of all the pci/agp card in your system, find your video card and tell me what it says for it, should say something like:
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

and post your /etc/X11/xorg.conf
I'll modify it, and setup your video card for you and see if that works.

---

### Post by mofomikeman on 2006-01-11
[QUOTE=Ocxic]choose auto for you vid card option, usually if there is a video card in the motherboard, the on board video gets disabled. if xorg still uses you on board video, install ubuntu, and when you get to the login prompt, login and type

lspci   - this will give you a listing of all the pci/agp card in your system, find your video card and tell me what it says for it, should say something like:
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

and post your /etc/X11/xorg.conf
I'll modify it, and setup your video card for you and see if that works.[/QUOTE]
I'm at school, ill do it tonight.  How could I save it to one of my NTFS partitions, they aren't listed in linux (i dont think) :-/.

---

### Post by mofomikeman on 2006-01-11
[QUOTE=Ocxic]choose auto for you vid card option, usually if there is a video card in the motherboard, the on board video gets disabled. if xorg still uses you on board video, install ubuntu, and when you get to the login prompt, login and type

lspci   - this will give you a listing of all the pci/agp card in your system, find your video card and tell me what it says for it, should say something like:
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

and post your /etc/X11/xorg.conf
I'll modify it, and setup your video card for you and see if that works.[/QUOTE]
Ok I'm home now.  How would i post the lspci output and my /ect/X11/xorg.conf, considering I do not see the linux partition in windows?  If there is a command to logon to an ftp server, I could upload it to my host and then pull it off when I boot back into windows.

---

### Post by Dr. Nick on 2006-01-11
You are right about the pci slot thing, The following will help you fix that without a reinstall.
 
If you are at a text login prompt then do this
 
login, then run **sudo nano /etc/X11/xorg.conf **look for the BusID option under the device section. My bet is that it says BusID "PCI:0:2:0" which is for your onbard. If you plugged in a AGP card then change that to 
BusID        "PCI:1:0:0"
make sure the driver is nv and if you want type something into the identifier field instead of intel....
then save using ctrl+x and exit. back at command line type **sudo halt** to shutdown and then make sure your monitor is plugged into your nvidia card. Turn it back on and it should work.
I dont think their is a PCI version of the 5500, but if their is it will be a different busid then the agp.

---

