---
title: "drive formatting problem"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Niall Flinn on 2005-12-05
Hi folks,

I'm moving to Ubuntu from Windows, and things seem to be going pretty well, but I've just physically moved one of the drives from my XP box into my shiny new linux box, and I'm having some problems reformatting it. It's ntfs at present and I'd like to make it ext3, but every time I run mkfs.ext3 on the drive, I get the following error:

**/dev/hda is apparently in use by the system; will not make a filesystem here!**

I've checked that the drive isn't mounted, and I've tried rebooting and checking that it's not listed in fstab, but to no avail - what am I doing wrong?

Cheers,

Niall

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=Niall Flinn]Hi folks,

I'm moving to Ubuntu from Windows, and things seem to be going pretty well, but I've just physically moved one of the drives from my XP box into my shiny new linux box, and I'm having some problems reformatting it. It's ntfs at present and I'd like to make it ext3, but every time I run mkfs.ext3 on the drive, I get the following error:

**/dev/hda is apparently in use by the system; will not make a filesystem here!**

I've checked that the drive isn't mounted, and I've tried rebooting and checking that it's not listed in fstab, but to no avail - what am I doing wrong?

Cheers,

Niall[/QUOTE]

It might be easier to just use fdisk or cfdisk on it.

---

### Post by Ocxic on 2005-12-05
if your going to do a freash install, try letting the ubuntu partitioner format and partition the drive for you during setup.

---

### Post by Niall Flinn on 2005-12-06
Thanks for your replies!
I've already had my Ubuntu system running for a few days, so I'm not doing a fresh install - I kept this drive in my XP box in case I had to go back to Windows for unrelated hardware reasons, but those have been resolved now, so I'm keen to get the additional storage online.

I'll give fdisk a shot this evening...

Niall

---

### Post by bunty on 2005-12-06
are you sure you mean to format hda ?? That is the disk itself not a partition.

my guess is that you want to reformat /dev/hda1 

or much more likely hdb1 or hdc1

what device is your ubuntu on? where have you plugged the xp disk into ? I doubt it is the primary master on your Linux system.

If that does not make you realise your mistake post some more detail so we can give precise advice.

:cool:

---

### Post by Gray. on 2005-12-06
Maybe you could use Gparted?
```
sudo apt-get install gparted
```

---

### Post by Niall Flinn on 2005-12-07
Well, basically I wanted to totally wipe the disk and make a new partition - I ended up using fdisk to destroy the old partitions and create a new one (hda1) and then mkfs to create an ext3 filesystem in it. I would have used fdisk for the filesystem too, except that I couldn't see anything called ext3 in the list it gave me to choose from...

The reason this disk is called hda is that Ubuntu is on a SATA drive called (IIRC) sda, so the new drive is the first ATA/IDE drive in the machine, which is presumably why it's been designated hda...

One more question: I edited fstab to mount hda1 at boot, and I basically copied the settings from the primary drive listed a couple of lines above - it seems to work fine, but I don't actually know what those settings are doing - can someone point me to a document that explains what they mean?

Thanks again,

N

[QUOTE=bunty]are you sure you mean to format hda ?? That is the disk itself not a partition.

my guess is that you want to reformat /dev/hda1 

or much more likely hdb1 or hdc1

what device is your ubuntu on? where have you plugged the xp disk into ? I doubt it is the primary master on your Linux system.

If that does not make you realise your mistake post some more detail so we can give precise advice.

:cool:[/QUOTE]

---

