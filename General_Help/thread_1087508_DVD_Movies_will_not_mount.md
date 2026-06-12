---
title: "DVD Movies will not mount"
date: 2009-03-05
forum: General Help
---

### Post by teropita on 2009-03-05
I am using Ubuntu 8.10.

If I put a data DVD into the drive it is read fine a DVD symbol comes up on the desktop and if I double click on the symbol I can check out the contents of the DVD.

If I put a Movie DVD in the drive I get an error the it will not mount.

fstab line is
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Is there a setting I need to change?

---

### Post by jolx on 2009-03-05
EDIT: sorry i can't help :(

---

### Post by jolx on 2009-03-05
Well if you just want to watch the dvd, you could install vlc and then just select 'open disc' from the vlc menu.


or to see if it will mount if you create a folder on the desktop, say *'a'*, then run the following command from the terminal:
```
sudo mount /dev/dvd ~/Desktop/*a*
```

where *a* is the folder you just created

---

### Post by teropita on 2009-03-07
VLC says 

DVDRead could not open the disk "/dev/scd0".

if I

sudo mount /dev/dvd /home/steve/Desktop/dvdtest

mount: No medium found

Any ideas?

---

### Post by teropita on 2009-03-07
Just had  a thought, could it be something to do with the way it is installed / cabled.

My motherboard only has 1 IDE connector. I have the cable coming off the motherboard and plugged into an IDE drive first (the boot drive) the last plug on the cable then goes to the DVD drive.

The IDE Hard Disk is set as master, and DVD drive is set as slave. I don't think I can use cable select as I understand the first plug is the slave and the last plug is the master, so that would be backwards to what I want.

The cables will not reach the other way around.

The only other thing is if I make the IDE hard drive the slave and the DVD drive the master would that cause me any problems. I just assumed that the Har Drive has to be master and the DVD drive slave.

---

### Post by linuxuser21 on 2009-03-07
Do you have restricted formats installed?  You need it to play encrypted DVDs.

---

### Post by teropita on 2009-03-08
I'm not sure about the restricted formats. I will check it out. but I plan to play around with the master slave setup and cabling first.

---

### Post by linuxuser21 on 2009-03-10
[This]("https://help.ubuntu.com/community/RestrictedFormats") will tell you about the restricted formats and how to install them.

---

### Post by teropita on 2009-03-12
It seems that I have 3 issues that are preventing Movies from being played.

Issue one was the DVD drive on the IDE connection. I have now installed a new drive which is a SATA drive. Now when I install a DVD I get an icon on my desktop and I can browse the files on the DVD. So that issue is solved.

Issue two is the restricted formats - I have now installed the Ubuntu restricted extras so the movies should be supported. I also installed the libdvdcss2 package so I should be able to view encrypted DVDs.

Issue 3 is the regionset. I still cannot view a movie, and I think this is because the region is not set in the DVD drive.
I have installed regionset and run it. I get an error to the effect that there is no DVD in the drive, however there is a DVD in the drive and it is being read ( I get the icon on the desktop).

So it seems that somehow I need to set the region but Regionset reports that I do not have a DVD in the drive. Any ideas how to proceed from here?

---

### Post by teropita on 2009-03-13
OK, I think I have it sorted. I tried all sorts of disks in the drive buy I couldn't get regionset to work. Then I found a suggestion to 

sudo rm /etc/udev/rules.d/70-persistent-cd.rules
then reboot.

Once I had rebooted I was able to set the region with regionset and now I can play DVDs

---

