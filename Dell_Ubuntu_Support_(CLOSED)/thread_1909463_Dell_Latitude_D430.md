---
title: "Dell Latitude D430"
date: 2012-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rithwik on 2012-01-15
i have a Dell Latitude D430 and i hav ubuntu 11.04 installed in it.i am not able to get the network drivers to work at all.i have tried restricted drivers and everything else.any suggestions?
 
 
Rithwik
:popcorn:

---

### Post by mikewhatever on 2012-01-15
Make sure to enable the recommended restricted driver, and reboot. It should work after that. If you aren't, for some reason, not able to do it, specify why not.

---

### Post by rithwik on 2012-01-17
thanks,
 
but whenever i click on the network icon and under wireles it says firmware missing.
 
rithwik:-(

---

### Post by carl4926 on 2012-01-17
Post result of

```
lspci -nnk
```

---

### Post by mudguts on 2012-01-19
That's odd as I have a D430 and it picked up all the drivers on a 11.04 install 32bit.  I then upgraded to 11.10 and it's all good.

---

### Post by sousuke on 2012-01-22
You can try installing this:

firmware-b43-installer

and then reboot.



It worked on my Latitude D430 running lubuntu 11.10

---

### Post by rithwik on 2012-01-25
thanx it worked.life with 11.04..:p;):D:o:):P:):)

---

### Post by nclay on 2012-03-29
I just loaded Ubuntu 11.10 on a D430 laptop and could not get the wireless driver to work until I loaded the firmware-b43. But once I reboot the system the wireless driver disappears again even though it shows that B-43 is still installed.

configuration: latency=0

any thoughts?

---

### Post by daz23 on 2012-04-27
I've had to do the following to get the wireless to work on a Dell d430 or Dell d830 for the last 3 or 4 Ubuntu releases. 

sudo apt-get remove bcmwl-kernel-source

sudo apt-get install firmware-b43-installer b43-fwcutter

---

### Post by crodler on 2012-05-04
After upgrade from 11.10 to 12.04 i get ata1: SRST failed (errno=-16)
error. HD works well when starting WinXP partition and also when mounting linux partitions under rescuecd livecd dont give any error running several hours.
When starting 12.04 sysatem gets frozen just after starting gui.

---

### Post by crodler on 2012-05-05
Solved:
Problem was BIOS version A05. After update to BIOS version A09  ubuntu 12.04 now starts and works. But sometimes access to harddisk is very slow. Seems it needs some finetuning.

---

### Post by crodler on 2012-05-05
Solved:
Problem was BIOS version A05. After update to BIOS version A09  ubuntu 12.04 now starts and works. But there are still some

---

