---
title: "Creating a duel boot"
date: 2006-06-26
forum: Desktop Environments
---

### Post by L2wis on 2006-06-26
Hey all, 

Question: **_How do you create a duel boot? Is there a program that can do this automatically?_**

Background info:

I firstly installed ubuntu 6.06 and found it great but because i couldn't play battlefield 2 i decided to gpart my Hard drive 50% split into ntfs and then linux. I then installed windows onto the newly created windows half of the hard drive. This is where the problem has occured though, because now my system automatically boots into windows.

Is there a program you can run that detects installed o/s' and writes a boot file? Or does this have to be done manually?

Thanks in advance.

Lewis

---

### Post by Ramses de Norre on 2006-06-26
You'll need to boot up a live disc, then run this commands from a terminal: ```
grub
root (hd0,1)
setup (hd0)
quit
```
With: 

(hd0,1) the partition containing your /boot/ folder, the first digit is which hard disk and the second one which partition, both start counting from zero so if  your /boot/ folder is on the second partition of your first harddisk it's (hd0,1).

(hd0) the partition to install grub on, hd0 represents the mbr and I think this is were you'll want it (otherwise you'll need to chainload grub with another bootloader).

EDIT: running "sudo update-grub" after all these steps seems like a good idea to me ;)

---

### Post by shawnrgr on 2006-06-26
the best / safest way to dual boot is to install windows FIRST, the install linux. Ubuntu setup should automatically see the windows os and set it up in grub.  Thats how I did it and i havn't had a any problems.

---

### Post by Ramses de Norre on 2006-06-26
That's true, but this is far easier then deleting ubuntu, installing windows and then reinstalling ubuntu.

---

### Post by L2wis on 2006-06-26
```
grub> root (hd0,1)

Error 21: Selected disk does not exist

```

it doesn't pick up on anything, my partitions are as follows:

[IMG]http://img78.imageshack.us/img78/1584/screenshot4ru.png[/IMG]

What do i need to tell grub?

---

### Post by Ramses de Norre on 2006-06-26
(hd0,0) if it's the first hard disk in your system, if that doesn't work: have you got more than one hard disk and how are they connected?

---

### Post by L2wis on 2006-06-26
[QUOTE=Ramses de Norre](hd0,0) if it's the first hard disk in your system, if that doesn't work: have you got more than one hard disk and how are they connected?[/QUOTE]

I've only got the one hard drive it's just conected as master. I'll try hd0,0.

It's still saying Selected disk does not exist =/

---

### Post by Sonofmoog on 2006-06-26
A solution you might consider is to boot Ubuntu from Windows.  It is not difficult, and it is the setup I use.  Here's how:



1) From the LiveCD, open a terminal, and issue the following command:

```
dd if=/dev/hda1 of=/home/$USER/ubuntu bs=512 count=1
```

Substitute your user name for $USER.

This copies the boot sector of your Ubuntu partition to a file.  

2) Copy the file to floppy or CD, or email it to yourself as an attachment.
3) Load XP and save the file to the root directory of C:
4) Open boot.ini, and add this line

```
c:\ubuntu="Ubuntu"
```

5) Restart XP, and you'll see a multi-boot window.  Select Ubuntu, press <Enter> and if all went well, the next thing you should see is GRUB

HTH

---

### Post by L2wis on 2006-06-27
[QUOTE=Sonofmoog]A solution you might consider is to boot Ubuntu from Windows.  It is not difficult, and it is the setup I use.  Here's how:



1) From the LiveCD, open a terminal, and issue the following command:

```
dd if=/dev/hda1 of=/home/$USER/ubuntu bs=512 count=1
```

Substitute your user name for $USER.

This copies the boot sector of your Ubuntu partition to a file.  

2) Copy the file to floppy or CD, or email it to yourself as an attachment.
3) Load XP and save the file to the root directory of C:
4) Open boot.ini, and add this line

```
c:\ubuntu="Ubuntu"
```

5) Restart XP, and you'll see a multi-boot window.  Select Ubuntu, press <Enter> and if all went well, the next thing you should see is GRUB

HTH[/QUOTE]

When i try and execute that command from the live CD i get this error:

**dd: opening `/home/l2wis/ubuntu': No such file or directory**

Where would the copied file get sent to if it did work?

Also from the live cd if i try and browse the files from the last installation (to check the directorys) I get this error:

[B]error: device /dev/hda1 is not removable
error: could not execute pmount

error: device /dev/hda2 is not removable
error: could not execute pmount
[/B]

for both partitions!? Is something not right?

---

### Post by Sonofmoog on 2006-06-27
[QUOTE=L2wis]When i try and execute that command from the live CD i get this error:

**dd: opening `/home/l2wis/ubuntu': No such file or directory**

[snip]

Is something not right?[/QUOTE]


Oops!  My bad.  I didn't remember at the time that your home partition on the hard drive would not be mounted.  

What would likely be easiest would be to boot from the livecd, adding the option 

```
fstab=rw, auto
```

I'm not familiar enough with the Ubuntu livecd to know whether that option is even available.  If it isn't, then you need to mount the filesystem.  

Open a console, and issue the command

```
Mkdir /$DIRNAME
```

Replace $DIRNAME with the name you choose.  Include the / so the directory is below the / directory in the hierarchy, and not buried someplace.  You may have to preface the command with sudo

Then, issue the command

```
mount -t ext3 /dev/hda1  /$DIRNAME
```

again, replacing $DIRNAME with the name you chose.  Again, preface the command with sudo if necessary.  Then repeat what I suggested earlier.

Your problem is complicated because none of the partitions on your hard drive is writeable, and neither is the LiveCD, so even if you create the file, you are stumped for a place to put it.  

If you have a floppy drive, you can try copying to a floppy, in which case the command would be:

```
dd if=/dev/hda1 of=/dev/fd0/Ubuntu bs=512 count=1
```

Good luck and HTH

---

### Post by L2wis on 2006-06-28
[QUOTE=Sonofmoog]
If you have a floppy drive, you can try copying to a floppy, in which case the command would be:

```
dd if=/dev/hda1 of=/dev/fd0/Ubuntu bs=512 count=1
```

Good luck and HTH[/QUOTE]

All of it is working so far, i.e i've mounted the drive, but i don't have a floppy drive i have a usb pen drive. When i right click to find out it's path it says /media ? What should i put in the second section of the command to copy the file?

I copied the file to my usb drive after some trail and error, and then followed the rest of ur instructions.

When i clicked to boot ubuntu nothing happened there was just the little underline thing flashing in the top left corner =/ I'm guessing the info in the file isn't right or something. The file didn't have any extention, should it have?

---

### Post by Sonofmoog on 2006-06-28
[QUOTE=L2wis]
[snip]

When i clicked to boot ubuntu nothing happened there was just the little underline thing flashing in the top left corner =/ I'm guessing the info in the file isn't right or something. The file didn't have any extention, should it have?[/QUOTE]

No, an extension is not necessary, though some append the extension "bin" to note this is a binary file .. 

As for your problem at hand, we are not finished yet.  Here are two more procedures to try.

First:
1) Mount file system as explained earlier
2) Issue the revised command

```
dd if=$MOUNTPOINT of=$USBSTICK/Ubuntu bs=512 count=1
```

Substitute the full path of the mount point in if= and the full path of the USB stick in of=

Second:
1) Mount the file system as explained earlier
2) Issue the command

```
chroot $MOUNTPOINT
update-grub
```

update-grub is a shell script that should be on your system in /usr/bin, I believe.  If you get a file not found error, do a search using find or locate.  Try:

```
locate grub | grep bin
```

Finally, the attached link points to some expert advice on dealing with boot problems.  It is not specific to Ubuntu, but you may find it valuable ..

[www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html]()

---

### Post by L2wis on 2006-06-28
Finally got it all sorted :D It took a combination of things in the end. I used a boot tool called gag which helped me boot back into linux, but then i was stuck the other way round! (jeees lol) but reinstalled grub then edited the menu.lst manually and it's all good :D

Thanks a lot to every one that has helped me. Many thanks sonofmoog for your timely replys

---

