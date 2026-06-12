---
title: "Trouble with fglrx..."
date: 2005-12-11
forum: Desktop Environments
---

### Post by okt on 2005-12-11
I am using Ubuntu 5.10, I have an agp based X850XT, and I have been trying to get it set up properly.

I went and grabbed:
fglrx-control
xorg-driver-fglrx

Then I changed
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 XT (R481)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	VideoRam	262144
EndSection
```
to
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X850 XT (R481)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	VideoRam	262144
EndSection
```

 and when I restart X it blows up and gives me an error. Is there a log I can post to help diagnose the problem?

---

### Post by wounded on 2005-12-11
I believe /var/log/xorg.0.log is what you mean

When X errors it asks you if you want to view this log and you can look at it there. I think after it errors you will have to move a copy of it somewhere before you start X again otherwise it will be over written and won't help in diagnosing what is wrong (Though there is xorg.0.log.old so maybe it keeps track of the last two X starts? I dont know).

But if the error came up when you manually editted xorg, maybe you should just "sudo dpkg-reconfigure xserver-xorg" after logging in to have the amchine remake your xorg. Then just select the fglrx driver when it asks.

---

### Post by okt on 2005-12-11
[QUOTE=wounded]I believe /var/log/xorg.0.log is what you mean

When X errors it asks you if you want to view this log and you can look at it there. I think after it errors you will have to move a copy of it somewhere before you start X again otherwise it will be over written and won't help in diagnosing what is wrong (Though there is xorg.0.log.old so maybe it keeps track of the last two X starts? I dont know).

But if the error came up when you manually editted xorg, maybe you should just "sudo dpkg-reconfigure xserver-xorg" after logging in to have the amchine remake your xorg. Then just select the fglrx driver when it asks.[/QUOTE]

I tried running the "dpkg-reconfigure xserver-xorg" in the first place, and the same thing happened.

---

### Post by haykel on 2005-12-11
You should post the /var/log/Xorg.0.log file so that we can analyze the problem. In the meanwhile you could try to verify that the linux-restricted-modules package for your running kernel is installed. You can install it with:

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo depmod -a
sudo modprobe fglrx

then start X. Other wise you could try to install the drivers from ATI. Look here for more informations:

[BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

Good luck ;)

---

### Post by okt on 2005-12-11
Ok here is Xorg.0.log

Sorry for having to gunzip it, the file was pretty large.

After doing what the guide says to do X fails to start.

---

### Post by okt on 2005-12-11
Ok it would appear that this is where it goes wrong:
```

(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.20.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.20g1                           
(II) ATI Proprietary Linux Driver Build Date: Dec  6 2005 20:05:53
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.20.1-driver-lnx-232334
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

```

The thing is that my card is at "PCI:1:0:0" and it seem that fglrx is looking at "PCI:1:0:1...
[B]

MODS IF YOU WISH PLEASE MOVE THIS TO THE HARDWARE/VIDEO AND SOUND SECTION.[/B]

---

### Post by kroiz on 2005-12-11
my card is at "PCI:1:0:0" too.
also did you added the fglrx to /etc/modules ?
also  xorg-driver-fglrx creates a copy of xorg.conf prepanded with a long number look in /etc/X11 for it (you can recognize it by its date)

---

### Post by haykel on 2005-12-11
[QUOTE=okt]Ok it would appear that this is where it goes wrong:
```

(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.20.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.20g1                           
(II) ATI Proprietary Linux Driver Build Date: Dec  6 2005 20:05:53
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.20.1-driver-lnx-232334
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

```

The thing is that my card is at "PCI:1:0:0" and it seem that fglrx is looking at "PCI:1:0:1...
[/QUOTE]

This is not the problem. As you can see the first line states that the primary device is PCI 01:00:0, which is true. The other line is only a Warning (WW) and says that you didn't configure the secondary monitor connector. Can you post the right Xorg.0.log again (the other one was wrong).

I would also suggest to look at this VERY GOOD page (it's for Gentoo but is very interesting):
[Gentoo ATI Radeon FAQ]("http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html").
For you the questions 4.15 & 4.41 should be interesting. Try adding the following line to the Device section of xorg.conf:
ChipID 0x4b49  #Radeon X850XT

Bye

---

