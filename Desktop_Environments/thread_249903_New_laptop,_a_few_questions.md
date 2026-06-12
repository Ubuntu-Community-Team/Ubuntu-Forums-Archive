---
title: "New laptop, a few questions"
date: 2006-09-03
forum: Desktop Environments
---

### Post by mykrob on 2006-09-03
Hey-

YEsterday, i bought a new Compaq V5204NR laptop. First, i imaged the hard drive so if i ever sell it i can make it like it just came out of the box. Didnt want that recovery partition taking up my Linux space :)  Then i formatted and installed Mepis 6, which is based on Ubuntu 6.06.

I got the widescreen resolution working by some things i found on this forum

> 
Ubuntu allows one to select 1280 x 800 resolution, which is the right one. However, it adamantly wants to use 1024 x 768, which looks stretched and very ugly. A nifty program called 915resolution is need to hack what the BIOS tries to say. It's a very simple fix.

Use Synaptic to download 915resolution.

Open the terminal and type sudo gedit /etc/init.d/bootmisc.sh to edit the boot-up script.

Add /usr/sbin/915resolution 58 1280 800 before : exit 0 at the end of the script.

Restart the notebook and the resolution should look crisp and clean.


That worked great!
I need some help getting the wireless working. I belive it is the INtel wireless.. What information do you need from me to better assist me?

Also, I am running KDE as my dekstop environment. I need help making a keymod map to make the volume buttons work on the laptop.

Thanks,
-myk

---

### Post by jimbob on 2006-09-03
Install network-manager.

$sudo apt-get install network-manager

They finally got it fixed and it works great on my Toshiba laptop      
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mykrob on 2006-09-03
thing is, i cannot verify what chipset my wifi is.. the last two items listed when running lspci are:

0000:60:00.0 Network Controller: Broadcom Corporation: Unknown device 4311 (rev 01)
0000:08:08.0 Ethernet controller: Intel Corporation: unknown device 1092 (rev 01)


help?

---

### Post by jimbob on 2006-09-03
My guess is that it is the Broadcom and that is not real good news.

I have the Atheros chip which has been supported by the last few Ubuntu kernels.

If I was you I would search the forum for 'broadcom' to see what others have done to get it to woek.

Does the the output of '$ifconfig -a' show anything other than eth0?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mykrob on 2006-09-03
i got it working. Turns out the chipset IS broadcom and not INtel, like Compaq claimed it was...

I removed ndiswrapper, the version included was VERY outdated, and installed version1.23 from source. I got the windows drivers from the Compaq website and plugged them into ndiswrapper, and the wifi fired right up!



Now, the only thing left is figuring out how to adjust the video ram on this Intel 950G graphics chipset.. I do have 3d enabled, but cannot adjust the ram amount, even after adding the line

VideoRam 65536

to the device section in the xorg.conf file..

Any ideas?

Thanks,
-myk

---

