---
title: "Grub Error 18 - S.O.S."
date: 2005-12-23
forum: Desktop Environments
---

### Post by lostinpace on 2005-12-23
Please Help!!!

I got grub Error 18 and i can't boot my Ubuntu 5.10 and i have a paper on that OS thats due fri.

I have a 2 hardrives. 1. IDE Master-200gig Maxtor w/ windows xp  2. IDE Slave-80gig Maxtor w/ Ubuntu 5.10, my mother board is a Gigabyte (GA-7s748-L) w/ a slot A, 2500 Amd Athlon xp process, and i have 256 mb Ram.

The problem started when i tempararliy replaced the windows xp hd w/ a 20 gig hd with windows 98. When i did that Grub never came up and it atoumatically booted w98, but when i put my hd w/ windows xp back in my computer and booted it up, I got the Error 18 messeage. I am assuming that when  i installed Ubuntu after i had intalled windows xp, ubuntu installed Grub on the windows hd automatically. 

So, how exactly do i fix this problem?

---

### Post by morganw25 on 2005-12-23
I am a newb here but I would suggest the easiest way would be to not try and boot from the hard drive but install it as an alternate and try and use either another bootable HD or live linux distro to recover the paper until you can figure out the original problem.

---

### Post by lostinpace on 2005-12-23
That would be an easy solution except i'm short on hardrives and i'm not exactly shure how to put 2 Os on one hardrive, so yeah. Thanx any how.

---

### Post by morganw25 on 2005-12-23
You did state you could still boot up one of the HD's correct?

If you have access to a cd burner you can get online download and burn a live ubuntu distro. 

Once you do that you should be able to access the faulted HD and the floppy drive to copy the paper to.

---

### Post by amohanty on 2005-12-23
The reason GRUB did not come up is because grub typically resides in the MBR (if you did the default install). Per web definitions:

> Web definitions for MBR
	Short for Master Boot Record, a small program that is executed when a computer boots up. Typically, the MBR resides on the first sector of the hard disk. The program begins the boot process by looking up the partition table to determine which partition to use for booting. It then transfers program control to the boot sector of that partition, which continues the boot process. In DOS and Windows systems, you can create the MBR with the FDISK /MBR command. ...

Which means it was on the first sector on your primary master HDD. If you remove it and replace it, no grub, so no menu. If you intend to do that often you will have to install GRUB elsewhere, which gets quite complicated with a newbie. I woudl suggest plugging the xp and the Win98 HDD and adding an entry to grub.

HTH

---

### Post by briancurtin on 2005-12-23
if you really need the papers, i would pop in a liveCD (knoppix, ubuntu, etc) and mount the hard drive then copy the papers over to a USB drive. 

worry about this stuff later, dont keep yourself up all night and then do the live CD as a last resort. get the data you need right now since its due in a few hours

---

### Post by lostinpace on 2005-12-23
WOW, it magically fixed its self!!! Don't know if i really did anything different, but it works so I'm good to go.

---

### Post by towsonu2003 on 2005-12-23
[QUOTE=briancurtin]if you really need the papers, i would pop in a liveCD (knoppix, ubuntu, etc) and mount the hard drive then copy the papers over to a USB drive. 

worry about this stuff later, dont keep yourself up all night and then do the live CD as a last resort. get the data you need right now since its due in a few hours[/QUOTE]

I agree, forget about grub... maybe you could email the paper to a yahoo / gmail / hotmail account using a live cd? 

You could also go back to your setup which booted Wondows correctly and use this [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) to copy that file to windows from ubuntu partition. 

After you are done emailing (or copying to flash, or writing to CD), read through this long thing (not my creation):> One Way

Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

==========================================

Another Way

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
==Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

==========================================

Yet Another Way

1. Put in install CD
2. boot: rescue
3. grub-install /dev/hda (hda is boot partition)


---

### Post by briancurtin on 2005-12-23
[QUOTE=lostinpace]WOW, it magically fixed its self!!! Don't know if i really did anything different, but it works so I'm good to go.[/QUOTE]
email those papers to yourself ASAP or get them onto a USB drive before something does go wrong and you really do have to dig yourself out.

---

### Post by towsonu2003 on 2005-12-23
[QUOTE=briancurtin]email those papers to yourself ASAP or get them onto a USB drive before something does go wrong and you really do have to dig yourself out.[/QUOTE]
or better yet (are you done with the paper??) back up your drive / all data while you remember how the panic of loosing data makes you feel :)

---

### Post by briancurtin on 2005-12-23
this exact situation brought me to linux, by the way. my hard drive freaked out in windows and was "dead" for 4 days and it just started working magically so i drove to Best Buy immediately and bought DVDs, then backed everything up. it "died" like 20 minutes after the backups finished and then i said screw it, ive been wanting to try linux so i installed SuSE and it worked perfectly.

---

