---
title: "Restoring GRUB to MRB"
date: 2006-04-30
forum: Desktop Environments
---

### Post by Geffers on 2006-04-30
I recently lost my GRUB but using Super GRUB Disk ([http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)) have managed to boot my ubuntu system.

Now I'm having problems restoring GRUB via the command line   I can get to the GRUB prompt but if I type install I get 'unrecognised command' even though the help option shows install ](*,)

My Super GRUB Disk has an option to retore GRUB to MBR but what will that actually do, will I have to configure anything further or enter any paths at boot time.

The Super GRUB Disk is excellent but goes through various options before it actually finds my Ubuntu system so I'd like to get back to normal.

Geffers

---

### Post by Koybe on 2006-04-30
did you try grub-install /dev/hda ?

---

### Post by Geffers on 2006-04-30
[QUOTE=Koybe]did you try grub-install /dev/hda ?[/QUOTE]

Thanks for very quick reply :) 

To the best of my recollection I did, I'm not in Linux at the moment so can't check.

I printed out a document I found on the web for making a Simple GRUB Boot Floppy but each time I follow the instruction I get 'invalid command'.

But re your suggestion above; I think that is what my Super GRUB Disk can do, if I reinstall GRUB will I have to enter paths for / /boot vmlinuz etc.

Geffers

---

### Post by mayankgarg1 on 2006-04-30
Dear Geffer
Please see the following link
[/url]https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub[/url]
 Here follow the instruction given in "Using the LiveCD while preserving Windows Bootloader"
Just use the command setup (hd0) if you want to install GRUB in MBR in step no 6

---

### Post by Geffers on 2006-05-01
[QUOTE=mayankgarg1]Dear Geffer
Please see the following link
[/url]https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub[/url]
 Here follow the instruction given in "Using the LiveCD while preserving Windows Bootloader"
Just use the command setup (hd0) if you want to install GRUB in MBR in step no 6[/QUOTE]

Thanks, I'm getting there, I think some of my problems are typo errors eg, knowing if I need /dev or just dev for filepaths, plus I realise case is important but that can be an issue.

Geffers

---

### Post by adrian15 on 2006-05-22
[QUOTE=Geffers]I recently lost my GRUB but using Super GRUB Disk ([http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)) have managed to boot my ubuntu system.

My Super GRUB Disk has an option to retore GRUB to MBR but what will that actually do, will I have to configure anything further or enter any paths at boot time.
Geffers[/QUOTE]

If you only have a Linux OS installed on your hard disk Super Grub Disk will restore your grub boot. No need to configure anything further. The menu you had before reinstalling windows will appear again with all of its options.

If you have two Linux OS installed SGD searches for the first grub menu that it finds. In a future SGD will have an option to select manually which grub/distro boot to restore.

adrian15

---

### Post by zxcv70 on 2006-05-22
It worked very well for me (without writing anything).
Here are the steps:

1. Boot your computer with Ubuntu CD. 

2. Go through the install process until you reach "[!!!] Disk Partition." 

3. Select Manualy Partition. 

4. Mount the appropriate linux partions:
/
/boot
swap

DO NOT FORMAT THEM 

5. Finish the manual partitioning. 

6. Select "Yes" when it asks you to save the changes. 

7. It will give you errors saying that "The system couldn't install ....." after   that; ignore them. Proceed with selecting "continue" until you get back to the Ubuntu installation menu. 

8. Jump to "Install GRUB." 

9. Once it is finished, simply restart your computer. 

Good luck!

From: [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by Geffers on 2006-05-23
[QUOTE=adrian15]If you only have a Linux OS installed on your hard disk Super Grub Disk will restore your grub boot. No need to configure anything further. The menu you had before reinstalling windows will appear again with all of its options.

adrian15[/QUOTE]

I do have Ubuntu installed to hda3.

I've got a boot floppy now and use the command line from the GRUB prompt, I'm quite happy with this at the moment as it is making me understand Linux better.

Geffers

---

### Post by Geffers on 2006-05-23
[QUOTE=zxcv70]It worked very well for me (without writing anything).
Here are the steps:

snipped

Good luck!

From: [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)[/QUOTE]

Thanks, all advice welcomed to understand how it all works.

Geffers

---

