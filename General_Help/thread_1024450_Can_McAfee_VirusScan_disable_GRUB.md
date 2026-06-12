---
title: "Can McAfee VirusScan disable GRUB?"
date: 2008-12-29
forum: General Help
---

### Post by AMat on 2008-12-29
Firstly, I'm a GNU/Linux newbie, and an amateur computer user in general.

I have a multi-boot system with Hardy and Vista and am using GRUB as my boot loader.

Today I was playing around with McAfee VirusScan Enterprise 8.5i on my Vista partition. I was switching some settings, and one of the things I did was to set the on access scanner to prevent the use of tftp (don't ask why, I don't really even know what it is). I then ran a system virsu scan, a defragmentation, and then shut down the computer.  

The next time I tried to boot my laptop, I found it wouldn't work.  The machine kept cycling through the boot sequence, and whenever the hdd was up, GRUB stalled after saying it was loading stage 1.5. It did not display any error message.

I was flipping through the GNU grub manual and found that it uses tftp to boot an OS from a network image, which is not what I was trying to do. However, my best guess as to what happened is that preventing the use of tftp has caused GRUB to hang.

Questions:

Does VS even have the ability to do that from within the Vista partition?

Could there be any other explanation? 

Does anyone know how I can fix this problem? Right now my computer is useless.

If anything I've said above is technically incorrect, it's because I don't know what I'm talking about, please don't slay me, I need help :D.

---

### Post by Seks on 2008-12-29
to fix it, pop in a live CD and do this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I suppose it could have done something to your master boot record (but I don't really know, don't take my word for it), however since windows cannot natively read ext2/ext3 it can't break your grub config within /boot

---

### Post by caljohnsmith on 2008-12-29
Before you restore Grub via the thread that Seks linked to, it would be helpful to see if McAfee did overwrite part of Grub in your MBR (Master Boot Record), so you will know for sure if that is the problem. How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo dd if=/dev/sda count=100 | gzip -c > ~/Desktop/sda.MBR.gz
```
That will create a small "sda.MBR.gz" file that will have your HDD's MBR and also the sectors that would contain Grub's stage1.5 file. Please attach that file to your next post, and I can check it for you if you want to see if there is any evidence of McAfee changing Grub.

---

### Post by AMat on 2008-12-29
Thanks folks.

I used the info on the thread to get grub working again. 

As to what happened... I have a family member who is a tech guy with McAfee (ironically) ,and he'd never heard of VirusScan affecting a boot loader, but he doesn't know GRUB.

Anyhow, I have the gzip file and will take a look through the online BASH guides before I stick it on the web because I wouldn't mind having some idea what is in it first.

I mounted the vista partition and went through the McAfee logs while in Ubuntu Live and discovered that there was a whole lot going on under the hood after I changed the settings, but none of it seemed to have anything to do with GRUB... not that I would really know. I think I'll revert to McAfee's defaults. It's a shame, all I was trying to do was learn a bit.

For all I know it was something completely unrelated, it just seemed like an obvious first guess.

Anyway, once I'm convinced that I'm not giving away the key to my laptop I'll post the gzip file.

---

