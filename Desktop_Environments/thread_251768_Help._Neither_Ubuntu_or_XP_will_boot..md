---
title: "Help. Neither Ubuntu or XP will boot."
date: 2006-09-05
forum: Desktop Environments
---

### Post by Chake99 on 2006-09-05
Yes. What the title says is true. :( 

When I select normal Ubuntu from the grub menu I get to the login screen, and after typing in my password and login name it jumps to a black screen with text at the top right corner saying either 'frenris is tty1' (frenris is my user name) or 'frenris tty1' (cannot recall) before taking me back to the login screen. 

When I boot with XP I come to a black screen which says something along the lines of 
> 
Booting Microsoft Windows XP Professional

root (hd0,0)
filesystem type unkown, partition type 0x7
savedefault
makeactive
chainloader +1


Where it stays until I pull the plug.

This occured first (I believe) the third time I booted my computer since installing Ubuntu. I was trying to XP boot at the time, the first time since install. 

It is probably important that I think I botched the drive partitioning. Before the restart Automatix was unable to properly download and install the programs I wanted due to the fact it stated my drive was full, and during the original installation I dragged the slider for the partition all the way to the right thinking I was giving Ubuntu all of the available space on the hard drive (there were 11 gigabytes of 38 available). 

There was no way that my hard drive was actually full. 

Do you guys know any way to fix this? Using the second option of grub it looks like I was able to properly log on to a command line, although newbie that I am I can't really do much from that position. As well I beleive there was an option to edit how grub sought to boot up the computer...

Any help would be highly appreciated. Right now I'm writing this from the live cd, so my computer isn't *that* messed up, so there has to be someway to fix it, right?

(I'm sorry if this is the wrong forum but it appeared to be a specific support question as opposed to a more general newbie one)

---

### Post by Chake99 on 2006-09-06
*bump* Cany anyone help?

---

### Post by mmmpancakes on 2006-09-06
I'm guessing the best thing to do here would be to reinstall grub. Search the forums for help with that, then report back.

---

### Post by Chake99 on 2006-09-06
Thanks for the response. 

I re-installed Grub and there is no change to the situation.

I'm now sure that after login it reads "frenris tty1"

As well I looked up how exactly my partitions had worked out. It said the NTFS partition is at /dev/hda1 is flagged as boot and has 26 of 36 gigs occupied while my linux partition had reached completely full at 2.07 gigs.

When I try to browse the NTFS partition I am told I do not have the proper permissions. 

How do I get permissions to access the NTFS partition? (recover files?)

And what does "tty1" mean?

Currently I'm planning to see if a windows XP repair CD can rewrite the MBR and give me back access to XP. If so I'll most likely try to reinstall linux or Grub.

If the former doesn't work the contingency is to try and back up my hard drive by hooking it up to another computer and then reformatting it. 

Is there anything else I should attempt first?

---

### Post by mgmiller on 2006-09-06
Using the XP install CD, you should be able to repair your boot record and reenter XP.

Put your Windows XP installation CD in the CD-ROM drive and reboot the computer (be sure the BIOS is set to boot from CD). 
     1. Start the Recovery Console from the CD 
     2. Run Fixboot from the Recovery Console. 
     3. Run Fixmbr to reset the master boot record. 
     4. Exit the Recovery Console and reboot the computer. 

You may also want to try to roll the 2.7 Gig or so back into your NTFS partition using partition magic or similar.

There may also be an entry in boot.ini that mentions grub, if so delete it.

Then, you can try to reinstall Ubuntu again, this time, giving it enough hard drive space.

I personally don't dual boot.  It makes me nervous.  I have seperate computers for XP and Ubuntu and network them.

Good Luck

---

