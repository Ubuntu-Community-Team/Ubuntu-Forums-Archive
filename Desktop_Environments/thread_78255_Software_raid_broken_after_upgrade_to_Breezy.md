---
title: "Software raid broken after upgrade to Breezy"
date: 2005-10-18
forum: Desktop Environments
---

### Post by ioliver on 2005-10-18
I'm upgrading my 2TB server to Breezy.  This has one raid 5 array and one raid 0 array.  Neither came up after the upgrade.

The problem seems to be that nothing is creating the device nodes.  It took a lot of fiddling to get this working on Hoary, with the order of the hotplug, mdadm and fsck scripts needing to be changed so that the devices were there before mdadm tried to mount the arrays and fsck tried to check them.

Now it's all broken again.

I can make it work after booting with -
sudo mdadm --assemble -a /dev/md0 /dev/sd[a-d]

If I miss off the -a this command also fails.  What's supposed to create the devices at boot time?  How can I get it all working again?

Also, can someone advise on when I need an mdadm.conf? It doesn't seem to be required, in fact mdadm says it makes one if it doesn't exist.

Regards

Ian

---

### Post by ioliver on 2005-10-19
<bump>

No-one using software raid on Breezy who can give me a rough idea of how it's supposed to work?

Ian

---

### Post by ioliver on 2005-10-21
Elsewhere, I have found two bits of advice on this issue, but it isn't Breezy specific.

1)
In /etc/udev/links.conf
Add something like :
M md0 b 9 0

2)
Q: How do you make devices persistent in udev, so they stop getting 
created dynamically?
A: you can cd into /dev/ and ./MAKEDEV md, then cp /etc/md* to 
/etc/udev/devices/

I have looked in /dev on my problem machine, and /dev only has the /dev/md0 that I created myself using the auto switch to mdadm. I've now created the others by using ./MAKEDEV as per instructions (2)   But I don't understand what the cp is supposed to do. I have nothing of that name in /etc other than the mdadm directory and I don't have /etc/udev/devices

All advice welcome.

Ian

---

### Post by ioliver on 2005-10-21
To complete my monologue (is no-one else using software raid on SATA with Breezy?) here was my fix -

1) Use "MAKEDEV md" in /dev to create the device nodes.
2) cp /etc/rcS.d/S04mdadm-raid /etc/rcS.d/S31mdadm-raid

Step 2 make sure that raid arrays aren't assembled until hotplug has done its stuff.

All of this stuff was broken on Hoary, totally changed for Breezy, but still left broken. :-( :-( :-(

Ian

---

