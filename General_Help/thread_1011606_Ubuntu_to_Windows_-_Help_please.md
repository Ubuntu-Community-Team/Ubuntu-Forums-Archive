---
title: "Ubuntu to Windows - Help please"
date: 2008-12-14
forum: General Help
---

### Post by imtheguido on 2008-12-14
So, I've been trying to get my computer to run properly with Ubuntu 8.10 for litteraly 3 days straight with maybe 10 hours of sleep total. I give up. I cant get the video card drivers to be read properly, I cant run my games without having to run them through wine, when the video card driver did actually work, and even then the graphics where horrid in comparison.

I want to switch back, but now yet another problem arises. It wont let me. I try to run my Windows XP Professional disk in Wine and it gives me an error when trying to gather information for the re-format. Alright, so I will boot directly from the disk. I cant. I go into the bio's and tell it to boot from the CD first. I have 2 CD drives which DO work as they read any other disk including the install disk when ubuntu is running. I know the XP cd works without issues as my other computer boots from it just fine. But when trying to boot from it on this computer, I simply get a black screen that just sits there.

This is becoming a real hastle, and I've become VERY aggrivated. If someone could please help me get my system back running with windows XP it would be greatly appreciated. I don't want to give up on Ubuntu Entirely and will check back at a later date and see if perhaps the system is more reliable. I have no issues with XP like I do Ubuntu. I know Ubuntu is more stable of course, but I simply don't have the technical knowledge to run it properly. Please help!

---

### Post by eBoxNet on 2008-12-14
Insert your windows disk and restart the computer,then keep pressing f11 in order to get your m/b boot menu.

Select the cdrom (the one with the disk inside) and hit enter...keep pressing a key until you c the windows setup loder.

ps.ubuntu has nothing to do with it.its not even loaded when you are trying to boot from your cdrom.

If that don't work let me know.

---

### Post by imtheguido on 2008-12-14
I rebooted with the disk in as asked, and pressing F11 repeatedly gave me no such menue. I tried all the fkeys and none of them gave me any sort of menue.

---

### Post by eBoxNet on 2008-12-14
Ok,no prob it seems that your mob doesn't have this feature.
Login to your BIOS and go to boot menu setting,change the first and the second boot device to be your cdroms and disable any other boot devices (such as disks and boot from other source options)
then restart the computer with the cd inside the cdrom. keep pressing the spacebar ...hopefully you will get the windows installer.

---

### Post by imtheguido on 2008-12-14
I tried that just now, and like before, I get a black screen and it does nothing. Hitting the space bar repeatedly does nothing but make a very very very slight click that sounds like its coming from my Mobo.

---

### Post by eBoxNet on 2008-12-14
yes thats normal,i told u to hit the spacebar cause windows xp cd needs that in order to boot and sometimes it prompts so fast that users can't c it.

thats very strange..do you have any other bootable cd ? did you try to boot ubuntu live cd?

the only thing i can think of is that you have a prob with your win cd.


:confused:

---

### Post by imtheguido on 2008-12-14
My ubuntu live CD works just fine, and my second desktop is booting from the Windows CD perfectly fine. Im so utterly lost at this point. >.<

---

### Post by eBoxNet on 2008-12-14
did you change something on your BIOS (except the boot seq) ?
did you try to restore BIOS default configuration? and then config your boot seq?

---

### Post by imtheguido on 2008-12-15
I havent changed anything else in the Bios except the boot order. I will try to restore the factory defaults for the bios and then re-order the boots and try to boot from CD again.

---

### Post by eBoxNet on 2008-12-15
waiting for the good news (i hope) :lolflag:

---

### Post by ekolimits on 2008-12-15
y dont u just run ubuntu live cd and use the partition editor to wipe your partition into ntsc. or even wipe it clean then boot up you win xp cd.

---

### Post by TeXtonyx on 2008-12-15
> **imtheguido said:**
> So, I've been trying to get my computer to run properly with Ubuntu 8.10 for litteraly 3 days straight with maybe 10 hours of sleep total. I give up. 

I want to switch back, but now yet another problem arises. It wont let me. I try to run my Windows XP Professional disk in Wine and it gives me an error when trying to gather information for the re-format. Alright, so I will boot directly from the disk. I cant. I go into the bio's and tell it to boot from the CD first. I have 2 CD drives which DO work as they read any other disk including the install disk when ubuntu is running. I know the XP cd works without issues as my other computer boots from it just fine. But when trying to boot from it on this computer, I simply get a black screen that just sits there.

This is becoming a real hastle, and I've become VERY aggrivated. If someone could please help me get my system back running with windows XP it would be greatly appreciated. I don't want to give up on Ubuntu Entirely and will check back at a later date and see if perhaps the system is more reliable. I have no issues with XP like I do Ubuntu. I know Ubuntu is more stable of course, but I simply don't have the technical knowledge to run it properly. Please help!

------------------------------------

If there is something you need from Ubuntu, like settings that
work, important data files, pictures etc, back them up first.

UBCD is a rescue cd for Windows and Sysres is a better cd for Linux.
Or you can just get a Gparted cd. Maybe this problem was once
fixable but after 3 days of your efforts, I now doubt it.

This will also test that you have your cdroms set to boot in bios. 
Boot Gparted and delete all partitions on the drive and install XP. 
This will work unless you have an upgrade only XP cd. If it worked 
standalone before for a clean install, it should still work that way. 
Also if you have an old XP install disk without SP1 slipstreamed it 
won't recognized a drive which is greater than 137GB.

You may be able to control how much of the drive that XP uses
so that you can set some aside for Ubuntu. If not, after you
install XP and test it, use the same Gparted cd to resize XP
and create space for Ubuntu.

When you reinstall Ubuntu from the live cd, at Step 7, Advanced,
choose to install grub to the /boot partition of Ubuntu not MBR.
Boot back into XP and download free Bootpart which you can use 
to create ubuntu.bin and an "Ubuntu" entry in your boot.ini menu.
If you use Ubuntu more, make Ubuntu the default OS in boot.ini
and change the timer from 30 or 10, down to 3.

The advantage of this is that both OS are independent of each other.
If XP fails, you can still boot Ubuntu with a boot disk. Instead
if ubuntu fails, your XP OS is not impacted. Once in awhile the
grub install to the MBR pinches the boot capability of XP. So if
you install grub to the /boot partition this problem is avoided 
thus you don't have to fix what isn't broken. 

I don't like the philosophy of putting Windows users that are new
to Ubuntu into geeky high waters which all too often results in
hours of frustration for the less techie of the Windows converts.

Although the analogy isn't precise because Linux seldom gets 
infected by trojans, the last time Windows got a trojan it took
me 5 days to fix it. I learned and now I fix it with a backup
that takes 30 minutes to complete. No more beating my head against
a wall trying to get a false sense of pride from accomplishment
when what one really gets is a headache. I've seen some of these
how to install a high-end video card threads drag on for over 50 pages,
that's over 500 posts. I guess because I'm getting older because I don't
enjoy my masochism as much as when I was young, dumb and full of
vinegar, it's just no fun anymore. ):P (couldn't find beating head icon)

---

### Post by /////// on 2008-12-15
I've also had this problem before, but I'm not sure what causes it. I suggest you wipe your hdd. Boot Ubuntu LiveCD, go to system>administration>partition editor and delete all the partitions on the drive then try again. Or, if you don't want to do anything, you can boot the computer with the HDD/s unplugged, then after the windows install screen pops up, you can reconnect you're harddrives.

---

