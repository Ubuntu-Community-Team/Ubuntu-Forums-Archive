---
title: "Installing Ubuntu+GRUB = No Boot Menu?"
date: 2009-05-22
forum: General Help
---

### Post by Nightykk on 2009-05-22
Greetings.
I'll start out with "first time ubuntu/linux user", so please bare with me.
 
Anyways!
 
I just installed Ubuntu, first time without the Grub loader, that just resulted in not being able to boot into Ubuntu, but Vista and XP working fine, I did some searching but figured the easiest way would be to install Grub..
 
So I did it the easiest way and just reinstalled Ubuntu with the addition of GRUB this time.
 
When rebooting after the install I just get to the: 
 
Boot from CD...
Boot from CD...
GRUB
 
And nothing happens.. Restarted just to make sure, nothing.
I then tried with the live CD, did all the:
 
[FONT=monospace]Sudo Grub[/FONT]
[FONT=monospace]find /boot/grub/stage1[/FONT]
[FONT=monospace]root (hd0,4)[/FONT]
[FONT=monospace]setup (hd0)[/FONT]
[FONT=monospace]quit[/FONT]
 
[FONT=monospace]Still nothing.[/FONT]
 
[FONT=monospace]I tried looking in the:[/FONT]
gksu gedit /boot/grub/menu.lst. 
It's blank, thers nothing there.
 
I've then tried the ms-sys thing.. Didn't help anything.
 
 
Anyone that got a good idea about what I can do now?
I understand most technical terms etc. so please do make it complicated if that's what required.
 
Also I'm currently using 6 harddrives, Ubuntu being installed on a Samsung 500 with a 30GB Partition made for it, with a 5GB Swap Partition, it's normally drive "J:" in Windows, Having XP Installed on my 74GB Raptor (C:), Vista I'm not utterly sure wheres installed, but I'll figure out if that's needed.
 
Also, I would prefere just getting the Vista Loader back, the whole "staying with what you know".
- I also downloaded some EasyBCD that I tried in Vista, before the whole reinstalling Ubuntu, that didn't work though. I got past the being stuck on Grub, but it didn't want to load anything.
 
Best Regards
Rasmus, Denmark

---

### Post by rehilliard on 2009-05-22
How to Repair or Fix a broken Vista MBR:

To Restore Vista MBR, please use the following simple solution.

1. Start your computer from the Windows Vista Installation DVD
2. Press a key when prompted to continue
3. Choose your language, time, keyboard and click Next:

Select language and preferences
4. Next, click "Repair your Computer":

Repair your computer
5. Now, from the System Recovery Options dialog, select the "Operating System" you want to repair, then click Next:

System recovery options, choosing your Operating system
6. From the "Choose a Recovery Tool" dialog menu, select "Command Prompt":

Recovery Tool Command Prompt
7. Type the following into the "Command Prompt Window":

bootrec.exe /fixmbr
bootrec.exe /fixboot

8. Remove the Vista Installation DVD and restart your PC.

If all goes well, this process should have enabled you to restore your Vista MBR and you should now be able to boot back into your Windows Vista Operating system.

---

### Post by Nightykk on 2009-05-22
Was just doing that before you wrote it.. It.. Didn't work, nor did it find windows though, but I did get to the commandpromt and did the rest..

But I'll try scouting for some raid drivers for this motherboard and try it again.

Oh! I only did bootrec.exe /fixmbr though!
Could that be why?

---

### Post by rehilliard on 2009-05-22
Yes...you need to fixboot...

FIXBOOT
fixboot drive name:
Use this command to write the new Windows boot sector code on the system partition. In the command syntax, drive name is the drive letter where the boot sector will be written. This command fixes damage in the Windows boot sector. This command overrides the default setting, which writes to the system boot partition. The fixboot command is supported only on x86-based computers.

FIXMBR
fixmbr device name
Use this command to repair the MBR of the boot partition. In the command syntax, device name is an optional device name that specifies the device that requires a new MBR. Use this command if a virus has damaged the MBR and Windows cannot start.

---

### Post by Nightykk on 2009-05-22
Righty, if everything goes right, I'll probably not get back to you.. But if it fails.. ;D
Hehe.

---

### Post by rehilliard on 2009-05-22
because of my inability to "guide" grub to install on the desired disk...over and over and over...i've had to do this procedure plenty of times.

I finally just gave up, and let grub install on the 2nd disk (the non-boot disk in a dual-boot), and just use the bios boot-select screen to get into ubuntu. 

Something about mixing a PATA and SATA and bios reporting the PATA first and GRUB using hd0 nomenclature and linux using sda nomenclature...and don't get me started. 

I wish the installers could (a)detect the actual boot drive (fdisk shows it!) and (b)detect where the distro is being installed...and just SORT IT OUT!

Good luck!

---

### Post by Nightykk on 2009-05-22
It worked! Better then I'd have thought.. It got all the old drives showing up like they used to.
 
But! This brings me back to.. How do I set up the Ubuntu to show up and work correctly from the Vista Loader? 
I tried the things I could find on google, but when I choose one of the Ubuntu's GRUB just goes to a screen where I can click TAB to get a long list of commands.
 
Got Ubuntu GRUB
Ubuntu LILD (< or something like that)
and one more which I forgot the name of, from that EasyBCD
 
 
Thanks.
 
 
Edit: Oh, wrote just as you did.
Aye it felt wierd.. Some things could detect all my drives, others could not.. But they could both detect the right harddrive, the one with Ubuntu on it, also the drive which Vista64 is on.. I think anyways.
But my setup is screwed enough as it is..
 
Raptor (WinXP) as C in XP, Vista64 on a 500Gb drive, Ubuntu on a partition.. Ah.. Gives me a headache :p

---

### Post by rehilliard on 2009-05-22
Good for you!

Having Ubuntu show in the veesta loader can be done...i've read about it, but never actually tried. 

Found this: [http://ubuntuforums.org/archive/index.php/t-569506.html]("http://ubuntuforums.org/archive/index.php/t-569506.html")

Go for it!!

---

### Post by Nightykk on 2009-05-22
Hm, your right.. The just changing the boot options in the BIOS sounds alot easier.
 
But this can't be done right with a Partition that's in the "end of the drive".. Can it?
Sure been a while since I played around with this..

---

### Post by rehilliard on 2009-05-22
I've done that before...albeit using Grub.

boot sector - vista - ubuntu in the "last" partition.

this works JUST FINE, since there's no way to get tangled up...single drive situation.

My motherboard reports the 2nd drive (pata) first, no matter what the boot order is setup as in bios. Grub puts it's stuff in the right partition and seems to always use the mbr on the SAME DRIVE WHERE IT PUT IT'S STAGE FILES! Not all of the distros, mind you, but more than I care to count. 

I really need to either (a) drop windows and dedicate the whole thing to ubuntu or (b) use a 2nd machine.

Just keep your vista install disk close by. ;)

---

### Post by Nightykk on 2009-05-22
> **rehilliard said:**
>  
Just keep your vista install disk close by. ;)
 
Hehe, I will :p
 
Think I'll try Ubuntu out on a old PATA harddrive on my old (but not antique) computer and see how that works out.. Then I can decide if I'll go for it on this one again..
 
Think I'll try out Win7 for now on that Partition instead :-)

---

### Post by Nightykk on 2009-05-22
> **rehilliard said:**
> Good for you!
 
Having Ubuntu show in the veesta loader can be done...i've read about it, but never actually tried. 
 
Found this: [http://ubuntuforums.org/archive/index.php/t-569506.html](http://ubuntuforums.org/archive/index.php/t-569506.html)
 
Go for it!!
 
Oh, but that requires me to actually get into Ubuntu.. Which I can't.. Heh.

---

### Post by rehilliard on 2009-05-22
livecd, my son. 

boot on the ubuntu live cd and then you can mount your installation partition and then make the changes.

ex: 
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
ls /mnt/sda1

where /dev/sda1 is the drive where you installed ubuntu.

now you have access to that partition and all the files you need.

---

