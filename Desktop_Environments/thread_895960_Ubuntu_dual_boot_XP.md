---
title: "Ubuntu dual boot XP"
date: 2008-08-20
forum: Desktop Environments
---

### Post by finito on 2008-08-20
I have Ubuntu installed, I want to run Dual boot of WinXP, I want to know how to go about it if I want to keep grub.

---

### Post by falcon61102 on 2008-08-20
I'm guess that your GRUB is installed to the MBR as is default so once you install WinXP, boot up with a liveCD and reinstall your GRUB.  If you don't have a liveCD handy, I recommend the Super GRUB Disk.  It's a much smaller download and a great tool either way.

[www.supergrubdisk.org](www.supergrubdisk.org)

Just be careful when partitioning to make sure that you don't accidently delete your Ubuntu partition.  Also, just a word of caution, Windows doesn't like being the second OS on any setup so be patient if it gives you any problems, as they can be worked around.

---

### Post by J$oney on 2008-08-20
Windows does not erase the Grub boot loader it only places it's greedy self infront of it, remember grub must be first on the MBR to work, you can install XP and use a live disk to recover the boot loader. All you need to do is boot the live CD into the command shell and do the following:

grub> find /grub/grub.conf
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

This will place the grub boot loader before windows ntldr boot loader, and all is well again.

---

### Post by cooke77 on 2008-08-20
The way i got my "Ubuntu/Kubuntu"...to work, was that I 'formatted' the Partition (my 2nd hard-drive..250 Gig)....as an 'active partition'.
Then, I installed 'Ubuntu/Kubuntu'....via the "Install within Windows' method.
This DOES allow the Grub (For 'Dual-Boot' option)to function properly.

Proceed, with caution.

You may have to reboot, several times...... IF it (Linux) fails to loads, without instance.

Use the " Press 'ESC', to enter Menu. " option. (You have to the count of 7....to Enter.)
If you are having a problem..Starting.....you may have to go through all 'options' available to you. To find the one that WILL 'continue' the Installation..of Ubuntu/Kubuntu. (A Reboot is definitely 'required'...with EACH attempt. BUT, you will get there, to continue the installation.)
I have done this many times. I can almost do it....in my sleep.
(I have a 'APCI problem'...with mine, which is why I DO use the " Press 'ESC', to enter Menu." option. I'm using a Dual-core AMD CPU...the "APCI" function of motherboard is "Enabled" (greyed-out)...forcing me to do nothing else but to take the option (with APCI problems)).
Yours may differ...so, my 'caution'(to you)....is well-meant!
Ubuntu/Kubuntu may seem to take a long time to LOAD.... do not despair..it will, eventually.
You may wonder 'Why'...if it seems to be installing again!....when you have already installed it 'within Windows'.

(THIS is very normal....do not try to STOP it from doing SO! As this will certainly mess up the WHOLE installation process!)

Once it has loaded...all that is required...from you.....is to ENTER the PASSWORD you created......when you installed it, via the "Install within  Windows' set-up. 

If this happens, correctly....you are in. And, away, with using Ubuntu/Kubuntu.

If you do mess it up (The Installation).....ALL you have to do, is......to Restart!.....in Windows (XP/even Vista).

Then, go to "Add and Remove".......and 'uninstall' "Ubuntu/Kubuntu".

Once you have done this, look in the Partition/Hard-drive...where you installed "Ubuntu/Kubuntu"....to DELETE the 'Back-up Folder'. (And, YES, you can indeed safely DELETE this Folder.)
I use CCleaner...to do a complete 'tidy-up'...of my System, after this. (It does help, to clean out anything that is left over from the uninstalling process. I use CCleaner, for every uninstallation.)

You are ready.....to try again! (No harm has been done to my computer system...using the 'above' method. None whatsoever.)

Print this out, if you can, for future reference. (or, write it out, if you have no Printer.)

---

### Post by caljohnsmith on 2008-08-20
> **J$oney said:**
> 
grub> find /grub/grub.conf
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

Actually, that is dangerous advice, because that won't work unless Ubuntu *just happens* to be on his first partition, which it probably isn't if he installed it after Win XP. Also, in Hardy, there is no /grub/grub.conf file. It would be better to search for the stage1 or stage2 files to locate the correct Ubuntu partition:
```
sudo grub
grub> find /boot/grub/stage1
[will return Ubuntu partition in the form (hdX,Y)]
grub> root (hdX,Y)
grub> setup (hdX)

```

---

### Post by carolinason on 2008-08-22
Yeah the easier way is to install xp first, then ubuntu. It's all done for you. I don't think XP will have any updates that over write the mbr. Vista just did.

Or you can use SBM Smart Boot Manager
[http://btmgr.sourceforge.net/about.html](http://btmgr.sourceforge.net/about.html)
weird web page, but  great tool

---

### Post by nsche on 2008-09-04
I set up a flash drive with grub on it so after xp was installed I could just boot back into Linux and then do the grub setup stuff.

---

