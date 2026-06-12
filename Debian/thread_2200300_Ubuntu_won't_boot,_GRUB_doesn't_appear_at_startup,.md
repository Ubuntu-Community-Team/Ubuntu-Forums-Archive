---
title: "Ubuntu won't boot, GRUB doesn't appear at startup, boot-repair cancels itself"
date: 2014-01-18
forum: Debian
---

### Post by Thomas_Chilton on 2014-01-18
Hello!  This is my first post here.  I'm trying to install Elementary OS Luna on a desktop Dell, I understand it's based off Ubuntu 12.04.  The installation seems to go without a hitch, but when I start the computer, it boots right into Windows 7.  The GRUB loader that I'm used to seeing on my Win7/Xubuntu Lenovo doesn't appear.  I've read other posts where boot-repair is recommended, but every time I do an automatic repair, it returns with the message:
[INDENT]
grub-pc purge cancelled. Please report this message to [email]boot.repair@gmail.com[/email] 
[/INDENT]

The computer continues to boot straight into Win7 without giving any other options at startup.  Does anyone have any suggestions?

Many, many thanks in advance!

---

### Post by howefield on 2014-01-18
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by xSCCMx on 2014-01-21
Are you trying to dual boot? If so...
I think Windows might be at the MBR (Master Boot Record) go and download EasyBCD from Windows and Configure it to allow a boot from your Linux Partition... 

[https://neosmart.net/Download/Register/](https://neosmart.net/Download/Register/)

---

### Post by oldfred on 2014-01-22
We need to see why it will not install.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Thomas_Chilton on 2014-01-22
Thanks very much for your replies!

xSCCMx, I downloaded EasyBCD and ran it on the Windows OS, but it didn't seem to have any effect.  I added a new entry to the boot menu, selecting GRUB (Legacy) and the partition on which Elementary OS is installed.  On booting the computer, the option to boot either Win7 or Elementary was there, but when I select Elementary, it loads a black screen with a blinking cursor.  Am I doing it wrong?

oldfred, I'll create the report and post it here as soon as I can; the computer is at a friend's house.  Hopefully it'll be useful!

Once again, thank you VERY much for the replies!

---

### Post by Bashing-om on 2014-01-23
Thomas_Chilton; Hi !

While we await the Boot-Repair info:
this:
> 
but when I select Elementary, it loads a black screen with a blinking cursor. 

is indicative that the system can not load a graphics driver.
Can you boot to a terminal ? I am not familiar with easyBCD so unable to advise howso from there, but, would be instructive to see what is not going on from using a few terminal commands .

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by Thomas_Chilton on 2014-02-02
Alright, I'm back with a BootInfo report.  The link is [http://paste.ubuntu.com/6863675/](http://paste.ubuntu.com/6863675/).  I hope it's helpful.

Thanks for your reply, Bashing-om!  My apologies for responding so late.  I'm afraid I don't know how to boot to a terminal; I'm not all that experienced with Linux.  My two cents worth, EasyBCD seemed almost too easy to set up under the Linux tab, so I expect I forgot to do something to direct GRUB to the ubuntu partition, but I can't figure it out.

Any suggestions are much appreciated!!  Again I apologize for my lack of expertise in Linux.

---

### Post by oldfred on 2014-02-02
Right now you only have a Windows boot loader, so you are not loading grub2's boot loader. 
We tend to use grub to boot not EasyBCD, a few use it and say with Windows 7 it works.
You have grub2 not grub legacy.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

You can also use Boot-Repair to reinstall the grub2 boot loader.
You can then try booting the recovery mode.
What video card/chip does your computer have.

Grub2 is the boot loader whether you use EasyBCD or grub2 as the Boot Manager (to choose systems to boot). 
So either way you will have to modify grub2's boot parameters for your video.
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

---

