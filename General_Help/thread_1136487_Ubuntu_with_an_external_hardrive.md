---
title: "Ubuntu with an external hardrive"
date: 2009-04-25
forum: General Help
---

### Post by planegenius on 2009-04-25
I just got a great deal off of ebay on a 160GB USB Portable Western Digital External Hard Drive.  I want to partition 100 for backup and 60 GB for Ubuntu.  

Should I have any issue installing Ubuntu to this hardrive? 

My main concern- Will it recognize the hardware during installation?
                 
Will I still be able to choose between windows and Ubuntu on startup?

Thanks!

---

### Post by nandemonai on 2009-04-25
Should work fine, problem being, if you install grub to the main drive in your machine and the external drive isn't connected (or supported by BIOS) at boot then grub will crash and burn and you won't be able to boot anything.

Best bet is to make sure that you can boot from the external via BIOS and when installing Ubuntu to the external then install grub to the external also. Then you can use BIOS to choose which drive to boot from.

---

### Post by regor210 on 2009-04-25
If your computers Bios will Boot from USB and you install from a CD then yes. BUT! If you install Ubuntu from Windows Grub will be on the USB drive and you will need to have it plugged in to start  Windows.  The computer will not boot without your USB drive.

---

### Post by jwbrase on 2009-04-25
Well, unless your machine is fairly old, it should be able to boot from USB. My own Ubuntu installation is on an external drive, though I have it paritioned completely for Ubuntu, without the backup partition on it. I did have to fiddle around with menu.lst a bit to get it working, but it's fine now.

---

### Post by mdurham on 2009-04-25
Just a bit of advice before you try this. I would remove (unplug cables) the internal drive before installing on the external one. That way you should have a self contained system on the external usb with no interference. It also prevents the mistake of overwriting the internal drive.
Cheers, Mike

---

### Post by planegenius on 2009-05-01
Ok, it works! I did notice that GRUB will not load if my main hardrive isn't connected (despite the fact I unplugged it while installing Ubuntu) but that isn't that big of a deal since I keep that plugged in anyways.  Good news is that Windows still works just fine and more importantly so does Ubuntu.  Another machine converted to Ubuntu...

Thanks for all of your help! :KS

---

