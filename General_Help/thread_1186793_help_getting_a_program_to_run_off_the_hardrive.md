---
title: "help getting a program to run off the hardrive"
date: 2009-06-13
forum: General Help
---

### Post by wademunkey on 2009-06-13
I have an older laptop that i have set up with dual batteries to last me about 5 hours without being plugged in, the problem is that i have a repair manual for my car is on a cd.  I have to remove my cd drive to use the second battery.
I would like to be able to copy the program off of the cd and onto the hardrive so that i can run the program directly off the hardrive.  I have tried simply copying the entire cd off the cd to the hard drive, but it wont work properly, it still looks for the cd.  
I have heard of this being used on windows, but it was a very long time ago.
Thanks for any help.
Andrew

---

### Post by synapsys on 2009-06-13
Best way is to make an iso of the cd then mount it accordingly. First, pop the cd in the cd drive. Make sure it is un-mounted. Then open up a terminal:

Note! only use one of the dd commands.
```

cd /home/yourusername/Desktop
dd if=/dev/cdrom of=cd.iso       # for cdrom
dd if=/dev/scd0 of=cd.iso        # if cdrom is scsi
```

This will make an image of the cd on your desktop. To use it check this out.

[http://sprayfly.com/2009/06/06/ubuntu-904-mount-iso-image/](http://sprayfly.com/2009/06/06/ubuntu-904-mount-iso-image/)

---

### Post by wademunkey on 2009-06-14
thanks alot
ill give it a try

---

### Post by wademunkey on 2009-06-14
ok, so i created an iso image of the cd on the hardrive, then i used gmount-iso to mounth the iso folder to my desktop, but when i run the .exe file, it wont run because it is still looking for the cd.
I tried to do it in the commandline as you showed above, but i am not able to figure that out........ i am not sure why.
Any idea on what i am missing?
Andrew

---

### Post by wademunkey on 2009-06-14
ok, so i found that the .exe file was the only one on the copied version of the cd that had any problem whatsoever running.  The program actually runs in Firefox, so i can just open the main menu document, then navigate as if the cd was in the drive.
I am currently working on how to make a shortcut i can put on the desktop/ applications menu to open that one file.
Andrew

---

