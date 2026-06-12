---
title: "ubuntu won't start after electricity went down"
date: 2006-08-23
forum: Desktop Environments
---

### Post by dav1d on 2006-08-23
Hi, 

The electricity went down while booting (dont know exactly in what phase), and since then ubuntu won't come up. The boot sequense stops right after the following line:
running local boot scripts (/etc/rc.local) [ok]

Id appriciate any help.

David

---

### Post by dav1d on 2006-08-23
more info:
when starting in recvry mode, I get the following:
wait_for_sysfs: wating for '/sys/devices/platform/i82365.0/bus' failed

Is there some way to repare th file system using the live cd?

David

---

### Post by nzk on 2006-08-23
Do you mean a power surge? Because a power surge destroyed my oven, tivo box, and several other appliances not long ago.

---

### Post by bigken on 2006-08-23
Can you boot from the live CD ? there might be damage to motherboard
if you can get to desktop via the live cd im sure there will a fix have you tried googling the error report ;)

---

### Post by dav1d on 2006-08-23
I turned on the air conditioner, and the computer turned off. The ubuntu was booting at the time.

I can boot from CD, but I have to mount the hard drives (/ and /home) manually.
Where should I look for the error? Is there a "fix file system" utility, like chkdsk in windows?

---

### Post by bigken on 2006-08-23
try unpuging all your usb devices 1st then reboot the pc I once a similar 
problem and it was a usb hdd when i unplugded it all was well ;)

---

### Post by dav1d on 2006-08-23
unpuging?

anyway, I have no usb devices attached

---

### Post by Southeast First on 2006-08-23
My guess would be a hardware problem, like nzk bigken were saying.

Go into BIOS and see what temparature your chipset's clocking.

---

### Post by Tomosaur on 2006-08-23
You could try booting into the recovery mode and running 'fsck'. I think it's SUPPOSED to be run before the system fully boots, so try 'man fsck' first to see if you can set it to hijack the next bootup. It will check and repair your linux filesystem - hopefully that'll work out for you. MAKE SURE to read 'man fsck' first, it's very useful to know what fsck is telling you, and there's a few options in there you may wish to try out.

---

