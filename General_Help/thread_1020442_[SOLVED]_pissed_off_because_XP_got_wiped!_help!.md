---
title: "[SOLVED] pissed off because XP got wiped! help!"
date: 2008-12-24
forum: General Help
---

### Post by WillBMX on 2008-12-24
Right so I just upgraded my pc, new CPU, RAM, and most importantly HDD. I wanted to have ubuntu on my old 40gig IDE HDD and put windows XP on my new 160 gig SATA HDD. I have used ubuntu for a while, having dual boot on my old IDE HDD with 20gig for XP and 20gig for ubuntu.
So anyways I downloaded the alternate version (graphical version didn't work for me last time) of ubuntu 8.10 and put it onto a disc, went through the installation process, clearly stating that I wanted ubuntu on the 40 gig HDD. So ubuntu installs and I reboot, it says 'DISK BOOT FAILURE, INSERT SYSTEM DISK'. I tweaked for a while, then went into BIOS and told the computer to boot from the 160gig HDD. I rebooted and then I get 'GRUB loading...' I'm like wtf? because grub should be on the other HDD... I pressed Esc to get up the GRUB boot menu and all I have is Ubuntu, Ubuntu Recovery mode, and the swap partition... no XP. So has ubuntu wiped windows from the HDD? If so then I'm super pissed because I spent ages formatting the HDD last night, and installing XP, setting up drivers and other software... So I really hope I haven't wasted my time. I am hoping someone can tell me that all I need to do is add XP to the list for GRUB and it will all be OK...
The only reason I can think of for what has happened is that I told ubuntu to use the IDE drive for the root file system, which it has, but told it to format the SATA drive and install on there in the process by accident or something crazy like that...
I can see both the IDE and SATA drives right now, and the root file system is on the IDE drive. GRUB, however, must be on the SATA drive as I can only boot from there.
So....

---

### Post by kerry_s on 2008-12-24
just use your windows disk to fix mbr.

---

### Post by WillBMX on 2008-12-24
Won't that wipe GRUB and use the windows boot loader instead? because what I want is GRUB to see ubuntu and windows, rather than having to change boot priority between HDDs to boot different OSs...

---

### Post by AlexBellisBrown on 2008-12-24
You should try booting up with the Ubuntu live CD, and editing the menu.lst file then. Youll need to add an entry for windows.

However, weather it will be there or not is another question, ive always created a backup of the menu.lst file when ive done this sort of thing.

---

### Post by AlexBellisBrown on 2008-12-24
Look here : [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

Follow that to try and restore GRUB. Once thats done youll only be able to boot into Ubuntu until you edit the menu.lst file. But that will be quite easy.

Youll need to add:

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

To the menu.lst file. Look over the link i sent you and see if your able to do it. Post back here with any problems. :)

---

### Post by WillBMX on 2008-12-24
> **AlexBellisBrown said:**
> You should try booting up with the Ubuntu live CD, and editing the menu.lst file then. Youll need to add an entry for windows.

However, weather it will be there or not is another question, ive always created a backup of the menu.lst file when ive done this sort of thing.

OK thanks I'll give this a shot.

---

### Post by WillBMX on 2008-12-24
> **AlexBellisBrown said:**
> Look here : [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

Follow that to try and restore GRUB. Once thats done youll only be able to boot into Ubuntu until you edit the menu.lst file. But that will be quite easy.

Youll need to add:

title Windows XP
root (hd0,1)
makeactive
chainloader +1 

To the menu.lst file. Look over the link i sent you and see if your able to do it. Post back here with any problems. :)


OK so I did this and it didn't work, XP was on the list but it told me that there was no such partition when I selected it. I changed the '(hd0,1)' to '(hd0,0)' because I think that's the SATA HDD and the IDE one is hd0,1. It then said 'NTLDR not found'... so do you think maybe I need to restore the MBR from the XP CD or something like that?

---

### Post by WillBMX on 2008-12-24
EDIT: Problem sorted, thanks guys. I altered menu.lst so it made windows boot from hd0,0 and then used the XP Recovery Console to restore ntldr.

To help anyone else with similar problems: [How to restore ntldr]("http://pcsupport.about.com/od/fixtheproblem/ht/ntldrntdetect.htm")

---

