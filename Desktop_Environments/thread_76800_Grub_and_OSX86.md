---
title: "Grub and OSX86"
date: 2005-10-15
forum: Desktop Environments
---

### Post by mdeltito on 2005-10-15
Hey, im a fairly new user and im having some difficulty adding my osx86 install to gru so i am able to boot it. heres my setup

I have 3 partitions on one disk, 1st is osx, 2nd is main Ubuntu part, 3rd is 1gb swap space.
I installed osx first, on the 1st partition. Then i installed ubuntu to the 2nd, and i assume grub overwrites the mbr so i now have no way of accessing the OSX install. 

Any ideas? 
And, i have alot of trouble catching on to seemingly simple tasks, so forgive me if i must ask a few more questions to find out what you mean!

---

### Post by Hairy_Palms on 2005-10-15
sorry i dont have a solution, but osx86 as in youve got mac on a PC? 
id imagine that you need yaboot instead of grub as thats what macos recognizes but i dont know how you would do it on an x86 pc

---

### Post by mdeltito on 2005-10-15
Hmm....
there are many guides out there for using the windows boot loader to dual boot, i cant see why there isnt a way for grub to do it.

TY though, any other help is appreciated...

---

### Post by mdeltito on 2005-10-16
Okay, i found a solution from reading the GRUB documentation...
I edited the menu.lst file and added an entry for OSX, and then used the chainloder to call Darwin.

title Macintosh OSX86
root  (hd0,0)
makeactive
# chainload OS/2 bootloader from the first sector
chainloader +1

---

