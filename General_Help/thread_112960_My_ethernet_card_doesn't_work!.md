---
title: "My ethernet card doesn't work!"
date: 2006-01-05
forum: General Help
---

### Post by hardsteel on 2006-01-05
First of all, i'm sorry for all my mis-spellings, i don't speak English very well.

I ordered Ubuntu linux from shipit and installed it on my laptop Dell Latitude CPx.
Everything seems to be working fine, exept my wifi card. I cannot get it working.... The model is Trendnet tew-226pc. In the device manager, it tells me the vendor and the device name:
Vendor: Realtek Semiconductor Co., Ltd.
Device: RTL8180L 802.11b MAC

Device type is unknown. I have everything set up right in network-admin, I think. I'd be really frustrated if I couldn't get it working. 

Please, help me out,
Mattias

---

### Post by carlosqueso on 2006-01-05
I have the same chipset in my Dlink card...
[http://www.ubuntuforums.org/showthread.php?t=96989](http://www.ubuntuforums.org/showthread.php?t=96989) this is how I got it working.  If you need further help...post in either this or that thread.

---

### Post by hardsteel on 2006-01-05
sudo apt-get update

I need active internet connection? It's just that.. i dont have one ... or isn't internet necesarry?

---

### Post by hardsteel on 2006-01-05
sudo apt-get update

I need active internet connection? It's just that.. i dont have one ... or isn't internet necesarry?:confused:

---

### Post by hardsteel on 2006-01-05
sudo apt-get update

I need active internet connection? It's just that.. i dont have one ... or isn't internet necesarry?:confused:

---

### Post by carlosqueso on 2006-01-05
I think it is, but that step may be unnecessary, try typing [CODE]ndiswrapper -l[CODE]and see what happens.

---

### Post by carlosqueso on 2006-01-05
I think it is, but that step may be unnecessary, try typing ```
ndiswrapper -l
```and see what happens.  Also...you can download the packages from [http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils) this website and transfer them on floppy/cdrom/usbdisk

---

### Post by hardsteel on 2006-01-05
I cannot unpack the file! It says type not supported :(
ndiswrapper sais unknown command. Plz, can u be more detailed since im a very big noob in linux...

---

### Post by carlosqueso on 2006-01-05
Okay....I'll try.  First, go to the link in my last post.  Download ndiswrapper-utils, and copy it to your ubuntu system: click on i386, unless you have an AMD64 kernel (if you don't know, click i386).  Then choose a mirror near you and click on it (you may have to right-click and choose save as. I did for some weird reason).  Copy the .deb  file to a disk and to your ubuntu system.  Then try (from the directory to which you copied the deb file) ```
sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb
``` and  post back the output, because if this doesn't work, we'll have to troubleshoot.

---

### Post by carlosqueso on 2006-01-05
btw....I'll be offline for a while....so if you have problems, I'll get 'em tomorrow....good luck!

---

### Post by hardsteel on 2006-01-06
Big thanks to you carlosqueso i got it working! Thanks!

BTW, there is a mistake in your manual - not sudo ndiswrapper -i NET8180.ZIP but sudo ndiswrapper -i NET8180.INF  ;)) 

THANKS!!

---

### Post by hardsteel on 2006-01-06
BIG THANKS GOT IT WORKIN'!!! 


:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d:d

---

