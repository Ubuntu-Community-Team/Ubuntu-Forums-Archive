---
title: "vmware and usb devices"
date: 2006-09-16
forum: Desktop Environments
---

### Post by tomslopez on 2006-09-16
I'm using windows xp on vmware and I wanted to know if there is anyway to get the vmware to read the usb devices like a usb memory flash? if there is how how is it done?
Thank You

---

### Post by Scunizi on 2006-09-16
You have to enable usb in the vmware window before loading your image.  Linux & Windows can't share the same usb device at the same time.  Maybe all you'll have to do is unmount it in Ubuntu and it may automatically mount in windows!

---

### Post by Giggity on 2006-09-17
If it's a USB storage device of some sort, perhaps you could use Samba to make a network drive out of whatever folder the USB device gets mounted to, the same as would be done with a hard drive (which works perfectly for me, as long as I can get VMWare running, which hasn't been the case the past couple of days since the kernel upgrade).

[Here's a good link that you'll probably want handy...  "HOWTO: Setup Samba peer-to-peer with Windows"]("http://www.ubuntuforums.org/showthread.php?t=202605")

If you've already tried that, then I've got nothing for ya :( -- I'm still quite the newbie myself!

---

### Post by Robor on 2007-02-14
> **Giggity said:**
> If it's a USB storage device of some sort, perhaps you could use Samba to make a network drive out of whatever folder the USB device gets mounted to, the same as would be done with a hard drive (which works perfectly for me, as long as I can get VMWare running, which hasn't been the case the past couple of days since the kernel upgrade).

[Here's a good link that you'll probably want handy...  "HOWTO: Setup Samba peer-to-peer with Windows"]("http://www.ubuntuforums.org/showthread.php?t=202605")

If you've already tried that, then I've got nothing for ya :( -- I'm still quite the newbie myself!

I did this using that guide and it went perfectly.  I copied the data from my USB thumbdrive to my Ubuntu samba share (/home/samba).  I can read the directory from my VMWare WinXP virtual machine however any access (read, copy, write) is *SLOW*.  I'm trying to copy a 1.5MB file from my samba share to my XP virtual machine and it took about 5 minutes for the copy to even begin.  It's been another few minutes and the copy is maybe 5% done.  In fact, I just checked and it's a few minutes later and maybe 10% done.  

Cool idea but totally not functional in my setup.  :(

EDIT:  Unless I'm doing something wrong I would **NOT** recommend this (samba & VMWare).  The file copy I mentioned in my original post was taking so long I canceled it.  After that everything hung and the open local folder went to 'Not Responding' (explorer.exe = 99%).  I had to restart the virtual machine to get functional again.

---

### Post by Robor on 2007-02-14
Problem solved here:

> **GorBo said:**
> Has anyone managed to get USB working on VMware (guest OS WinXP) after the upgrade to Ubuntu 6.10? Previous solution (worked under 6.06) was to:

add **usb.generic.skipSetConfig = "TRUE"** to .vmx file of the virtual machine.

Thanks GorBo!

---

