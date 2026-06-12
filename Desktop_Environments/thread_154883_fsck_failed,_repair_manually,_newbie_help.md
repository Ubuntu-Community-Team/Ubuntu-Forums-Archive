---
title: "fsck failed, repair manually, newbie help"
date: 2006-04-04
forum: Desktop Environments
---

### Post by tiggertiffin87 on 2006-04-04
Here's what I've been getting when I've been trying to load Ubuntu.

LUncompressing Linux...OK, booting kernel.
Loading, please wait.

(then there's along pause)

*Starting RAID devices [OK]
*Starting hardware event daemon [OK]
*Creating initial device modes [OK]
*Setting disk parameters [OK]
*Checking root file system
/contains a file system with errors, check forced.
/:
Filesystem contains large files, but lacks LARGE_FILE flag in superblock.

/:UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (i.e., without -a or -p options)

[fail]

*fsck failed.  Please repair manually and reboot.  Please not that the root file
*system is currently mount read-only.  To remount it read-write:

*  #mount -n -o remount,rw /

*CONTROL-D will exit this shell and REBOOT the system.

Give root password for maintenance (or type Control-D to continue):

When I try entering the password it keeps telling me login incorrect.  I don't have any important files saved so am open to reinstalling as well.

---

### Post by dcstar on 2006-04-04
[QUOTE=tiggertiffin87]
.......
Give root password for maintenance (or type Control-D to continue):

When I try entering the password it keeps telling me login incorrect.  I don't have any important files saved so am open to reinstalling as well.[/QUOTE]
If it worked ok previously, and you do not have a working root password, then the only way to fix it is to do something like boot up the Ubuntu install disk, go to a terminal and manually run fsck from that.

Do a forum search for detailed instructions on how to do something like this.

If you edit /etc/default/rcS and make it:
```
FSCKFIX=yes
```
Then fsck will automatically run and try and fix any problems at boot-up.

It may be simpler to do a re-install, but that's up to you to decide.

---

### Post by CameronCalver on 2006-04-10
Hey dc star this is what hapened for me 
unexpexted consistency /run fsck manually

fsxk failed pleas repair manually 
please note that hte current root file system is currently mouned read only to remoun it read-write

niunt -n -o remoun rw

control d ill eit from this shell then reboot

bash lesspipe :comand not found

bash:dircoloures:comand not foun

root@(noe):~# 

what do u think about running ubuntu install disk if i do that and what do i type and will it cancel any of my paritions of does it just repair so i wont have to do the paritions again and for some reason i left it overnight and it said you system has errors it wen form 1 to 100 percent and i think it fixed buti  would like to just go on the ubuntu install cd and repair if it will not destroy anything on my hard drive

---

### Post by dcstar on 2006-04-10
[QUOTE=CameronCalver]
.......
what do u think about running ubuntu install disk if i do that and what do i type and will it cancel any of my paritions of does it just repair so i wont have to do the paritions again and for some reason i left it overnight and it said you system has errors it wen form 1 to 100 percent and i think it fixed buti  would like to just go on the ubuntu install cd and repair if it will not destroy anything on my hard drive[/QUOTE]

If it seems ok then it should be, if it has massive errors then fsck isn't going to be able to recover everything - something may have gone wrong with your hardware.

---

### Post by CameronCalver on 2006-04-11
hey i put the install disk and it came up will that thing do u want to install server or defualt the boot: i wrote boot:fsckfix=yes and it said boot kernal image not found or something like that do u wht went wrong

---

### Post by dcstar on 2006-04-11
[QUOTE=CameronCalver]hey i put the install disk and it came up will that thing do u want to install server or defualt the boot: i wrote boot:fsckfix=yes and it said boot kernal image not found or something like that do u wht went wrong[/QUOTE]
You may be better to download something like this:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by CameronCalver on 2006-04-11
i cant find what i need on that cd can u give me the exact link all i need it something to repair fsck

---

### Post by dcstar on 2006-04-11
[QUOTE=CameronCalver]i cant find what i need on that cd can u give me the exact link all i need it something to repair fsck[/QUOTE]
This is all I can offer:

[http://ubuntuforums.org/showpost.php?p=833916&postcount=8](http://ubuntuforums.org/showpost.php?p=833916&postcount=8)

---

### Post by CameronCalver on 2006-04-13
hey dc star i got ultimate boot cd but i dont know what to do to repair fsck

---

### Post by dcstar on 2006-04-13
[QUOTE=CameronCalver]hey dc star i got ultimate boot cd but i dont know what to do to repair fsck[/QUOTE]
Ok, I just booted up with it myself (you need the version with "INSERT")!!!

Select F7 to go to the INSERT system (which is Linux), then;
Select F3 to boot the recovery mode, then do the following at the # prompt:
```
fsck -y /dev/hd**xn**
```
where the "xn" is the designation for the filesystem you want to fix (mine was /dev/hda4, yours will probably be something different)

The "fsck -y" will automatically answer "Yes" to all prompts, so you don't have to sit over the keyboard hitting return many times........

---

### Post by CameronCalver on 2006-04-13
well in a 28.8k modem and i downloaded the basic version without insert and it has not stuffed up since i asked so im not going to worry bout it until it does not work again

---

