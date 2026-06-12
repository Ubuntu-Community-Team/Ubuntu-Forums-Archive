---
title: "Dual boot or not dual boot?"
date: 2005-12-14
forum: General Help
---

### Post by BobInIdaho on 2005-12-14
I am using the latest KDE Ubuntu and have my system set up to dual boot (have two hard drives, one for Ubuntu and one for XP) from a menu. What do I do if I don't want to dual boot anymore?  How do I restore my drives so that I can boot from one or the other by unpluging the Ubuntu drive or the XP drive?

Any help would be greatly appreciated...Bob:confused:

---

### Post by aysiu on 2005-12-14
I don't know if you can do that, honestly.

As I understand it, one or the other operating system has to be in charge of the Master Boot Record. If Windows is in charge and you remove Windows... it's not going to work. If Ubuntu is in charge and you remove Ubuntu... it's not going to work.

What's wrong with your current setup?

---

### Post by BobInIdaho on 2005-12-14
It works fine the way it is...I just wanted Ubuntu and XP to be a stand alone program. There is no way to restore the boot record of either drive then, is  that right?

Bob

---

### Post by aysiu on 2005-12-14
What do you mean by stand-alone programs?
Aren't they stand-alone now?
I'm not trying to be difficult--I just really don't understand what you're trying to accomplish.

So right now, you have them on separate drives. You have one boot menu from which you can select either OS to boot into.

If I'm understanding you correctly, you want them still on separate drives, but you want to be able to physically remove a drive and have the MBR automatically detect which one is still inserted...?

---

### Post by TudorB on 2005-12-14
If you want to remove Windows XP, just remove Windows XP statement from grub.conf (lilo.conf) file. For lilo, you must call /sbin/lilo after...
If you want to remove (k)ubuntu, use the windows xp cd, go to the recovery console, and use fixmbr to write a new configuration to your MBR. Of course, being a Microsoft product, fixmbr won`t even try to detect non-microsoft OSs, and it will always boot in XP.

---

### Post by Dynotrick on 2005-12-14
wouldn't each drive have it's own MBR ( i'm assuming you want only one drive plugged into the computer at a time )

---

### Post by korkow on 2005-12-14
If you really want to reamove it, open

> /boot/grub/menu.lst
and scroll to the very bottom of that. It should say something like:

> title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Then just delete it out and you should be good

---

### Post by mfarquhar on 2005-12-16
i beleive that there is a thing you can get where you turn a key on the front of the machine and it physically switches the connections for the hard drives. but i'm still looking in to this though

and the only way i know 
[COLOR="Red"][SIZE="4"]**_(don't listen to this unless no one else can help you)_**[/SIZE][/COLOR]
is to reinstall both OS's sepparately with only one HD on at a time

---

### Post by Emerzen on 2005-12-16
I had my PC set up that way until I figured out how to dual boot w/ one bootloader.  Yes, both disks have an MBR.  The BIOS only looks for the MBR on the disk you tell it to.  In any case, here's how I did it:

Go into my BIOS, turn one drive off.  Install whichever OS you want on the drive that is on.  Repeat for the other OS.  Now, you will have to go into your BIOS every time you want to switch OSs, but it works fine.

This was a giant PITA, so I don't know why you'ld want to do it if you have a working dual boot.

---

### Post by BobInIdaho on 2005-12-19
What I wanted is to be able to remove the XP drive and still have Kubuntu boot up.
Or....remove the kubutu drive and still have XP boot up.

But...you are all correct...that's a pain in the a$$ to do it that way so I'll leave it alone and dual boot off of the menu. 

Thanks all...some reallly good ideas were submitted. 

Bob:razz:

---

