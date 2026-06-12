---
title: "ATI Question"
date: 2006-01-06
forum: Gaming &amp; Leisure
---

### Post by Imexius on 2006-01-06
aaaaaaaaaaaaaaaaaaaaaaaa

---

### Post by Zeroedout on 2006-01-06
if you just want 3d acceleration, it just depends on your card; which ATI card do you have?

---

### Post by FizDev on 2006-01-06
I don't know about a command... but you can do it manually. Just change the config in xorg.conf

```
sudo gedit /etc/X11/xorg.conf

```

Go where it says something similar to this
> 
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Then change the "ati" to "fglrx" (assuming that you have already installed ati-fglrx)

---

### Post by Imexius on 2006-01-06
33232

---

### Post by FizDev on 2006-01-06
I believe that to install the drivers you must do
> sudo apt-get install xorg-driver-fglrx

I'm not too sure about this so you should take a look at his howto :
[http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")
Should do the trick ;)

Just make sure to do a backup of your xorg.conf before doing anything!

---

### Post by Imexius on 2006-01-06
000101010010101

---

### Post by zappa86 on 2006-01-06
Can you start X without the "noaccel" option if you make the driver the fglrx.?Make sure you have it installed. If you wanted to, you could also download the driver from ATI (i think its a newer version than you will get from synaptic).

---

### Post by Imexius on 2006-01-07
010100100101

---

