---
title: "How do you access compactflash drive when card doesn't automount?"
date: 2005-05-28
forum: Desktop Environments
---

### Post by cinematography on 2005-05-28
My compactflash drive no longer automounts when I put a picture disk in. Is there a program or a way I can access the files on that drive. 

Please Note: I'm a newbie.

---

### Post by thrift on 2005-05-28
[QUOTE=cinematography]My compactflash drive no longer automounts when I put a picture disk in. Is there a program or a way I can access the files on that drive. 

Please Note: I'm a newbie.[/QUOTE]
 you can try to open a terminal(right click on background and click open terminal) and then type some commands such as the following:

sudo bash
enter your password and hit enter
cat /proc/scsi/usb-storage

this should give you a list of all SCSI hardware Linux is aware of.  This should show an entry for your compact flash drive, as disks on a USB bus are accessed through the kernel's SCSI emulation.

In example my results of cat /proc/scsi/scsi:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: MAXTOR   Model: ATLAS15K_18WLS   Rev: DT60
  Type:   Direct-Access                    ANSI SCSI revision: 03
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic  Model: USB Storage-SMC  Rev: 0207
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 01
  Vendor: Generic  Model: USB Storage-CFC  Rev: 0207
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 02
  Vendor: Generic  Model: USB Storage-MMC  Rev: 0207
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi2 Channel: 00 Id: 00 Lun: 03
  Vendor: Generic  Model: USB Storage-MSC  Rev: 0207
  Type:   Direct-Access                    ANSI SCSI revision: 02

You can see the third device in the list is my CFC or compact flash drive.  Since it is the third device in the list it lets me know something about how Linux references the device.  The first device in the list is sda, the second is sdb, the third is sdc, and so on and so fourth.

so if you had your third SCSI device as the Compact flash drive you would do the commands I am about to show you in an attempt to gain access to it:

mount /dev/sdc /mnt
ls /mnt

If you have a differenct device, such as the first SCSI device, you would use that device to reference it, so for the first SCSI device you would try mount /dev/sdb /mnt

The ls /mnt is just a way to see a list of the files on the disk assuming the commands worked.  It is possible that right after the mount command Ubuntu could just show you the files in a new window.

If you can see the files on your compact flash disk when you ls /mnt and Ubuntu has opened no window for you to view them you can open nautilus(file manager) window and go to File->Open Location... Type in /mnt in the box and click open and you should have the ability to view your pictures.

When you are done looking at your pictures(before you remove the media from your compact flash drive) you need to type in the terminal:

umount /mnt/

This is to make sure the device can be removed safely.

Good luck, hope it works.

---

### Post by cohort on 2005-06-02
[QUOTE=thrift]mount /dev/sdc /mnt
ls /mnt[/QUOTE]
 And how does one get the CF card drive to automount when a card is inserted?  I can manually mount the "drive" just fine, but having it automount is **very** necessary for the application.

I checked all the settings in device manager..  automount policy is 1, is_mounted is always 0 (unless done manually).

---

### Post by thrift on 2005-06-02
For that...you submit a bug report I think.  There appears to be a lot of posts about this lately, so I imagine someone screwed something up.  I plan to do the same thing in a couple days if it's not fixed yet, as my compact flash drive is also...not automounting.

---

### Post by cohort on 2005-06-15
[QUOTE=thrift]For that...you submit a bug report I think.  There appears to be a lot of posts about this lately, so I imagine someone screwed something up.  I plan to do the same thing in a couple days if it's not fixed yet, as my compact flash drive is also...not automounting.[/QUOTE]
 Yeah, that'd have to be it - every other removable media I have automounts just fine, it's only CF cards that don't.  And they all worked in Warty, before I upgraded.

---

### Post by cohort on 2005-06-21
I should have posted this earlier, but here it is:
Opened new bug ([11878](https://bugzilla.ubuntu.com/show_bug.cgi?id=11878)) "CF cards don't automount under Hoary"

---

### Post by arunsub on 2005-06-21
I have the same problem. I do have additional issue. I format my CF card using the format option in the camera. When I try to mount the device, it says unknown format type. It works fine if I use KDE. It auto mounts in KDE and i could access the photos, but not in GNome. Any idea why?

---

