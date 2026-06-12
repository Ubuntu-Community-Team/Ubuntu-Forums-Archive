---
title: "Need some advice about GRUB"
date: 2006-01-17
forum: General Help
---

### Post by thespazzz on 2006-01-17
Specificly...

I currently Dual Boot UBUNTU and WINXP.. XP is for my two favorate Simulator Programs FS2004 and Orbiter which sadly will not run under WINE.

A few weeks ago my Video Card failed.  Being in preperations for an upcoming compitition for the Flight Sim I replaced my ATI card with an NVIDIA card.  Ubuntu "Bless it's little heart" had no issues detecting the change and running with the new drivers.

XP.... Well lets say I hate XP even more at the moment and I can't get more than around 1FPS in the sim.

After trying everything I know i've decided to just wipe and reload XP.. BUT if I do so... the XP installer will wipe out the Bootloader and I won't be able to access Ubuntu.

I've spent a LONG time to get Ubuntu where I want it and I sure as hell don't wana wipe it out.. So.. How can I do this and either....

A. NOT Wipe out GRUB
B. Backup and Reload Grub After I install XP

Any help will be appreciated.

---

### Post by thespazzz on 2006-01-19
**Bump**

---

### Post by goatflyer on 2006-01-19
I know Microsoft allows you to install Windows as a secondary OS, but there does seem to be issues.

[http://support.microsoft.com/search/default.aspx?query=partition+install&x=0&y=0&catalog=LCID%3D1033&spid=1173&qryWt=&mode=r&cus=False](http://support.microsoft.com/search/default.aspx?query=partition+install&x=0&y=0&catalog=LCID%3D1033&spid=1173&qryWt=&mode=r&cus=False)

Step 0: Make sure you have recent BACKUPs in case!

Now, you will need to make a backup of your MBR and maybe also of the boot record on your /boot volume using dd  These are just 512 bytes long each so you could tuck them anywhere

To make copies (assuming /boot is 2nd partition of /dev/hda ):

$ cd /somewhere/safe/maybe/a/temp/directory
#to copy MBR from /dev/hda
$ dd if=/dev/hda of=dev-hda-512.bin bs=512 
#to copy boot record from partition 2 (maybe not needed)
$ dd if=/dev/hda2 of=dev-hda2-512.bin bs=512 

Copy these files somewhere safe.  Make sure you have a Linux boot CD also 

(Ubuntu LiveCD works great)

Install XP, paying attention to Microsoft's gotchas (see link)
Don't wipe out your partitions!

Boot Ubuntu live CD, open a terminal window, mount the partition containing your saved boot records.

# restore MBR
$ dd of=/dev/hda if=dev-hda-512.bin bs=512 

Try to reboot.  It should come back grub since the Windows install should not have touched any partition you didn't tell it to touch.

If it still doesn't, the restore the boot record into your /boot partition.
$ dd of=/dev/hda2 if=dev-hda2-512.bin bs=512

---

### Post by aysiu on 2006-01-19
[HOWTO: Restore GRUB (if your MBR is messed up)](http://ubuntuforums.org/showthread.php?t=24113)

---

