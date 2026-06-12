---
title: "Command line Copy"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Emasters on 2006-10-03
How do I use the command line only to copy files form the hard drive to a CD burner.  I can't gt my GUI up and rrunning and I want to reformat the hard drive but only after I get a few files off.  All I have is the command line, so how do I get files off either to an email or to a CD?  Thanks in advance

E-

---

### Post by Emasters on 2006-10-03
How do I get files off my hard dirve using only command line?  Copy to CD I have to reformat because I have no GUI interface and I need some files.   I can't load new system into new partition because it is too small.  HELP!!!

---

### Post by DirtDawg on 2006-10-03
Use the "cp" command.
```
 cp /some/path/text.txt /whatever/path/text.txt 
```
where the first is the file to copy and the second is where it's copied to. Use "man cp" for more info.

---

### Post by az on 2006-10-03
[http://yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)

mkisofs -r -R -J -l -L /home/user1 | cdrecord dev=0,4,0 -v --eject speed=4 - 


I think you may have to use the dev=/dev/hdc (or whatever your burner is) syntax since 2.6 kernels do not use scsi emulation anymore....  And you don't have to use 4x speed, you can go as fast as your burner can go.  I think burnfree is on by default.

---

### Post by mitch.c on 2006-10-03
> **Emasters said:**
> How do I get files off my hard dirve using only command line?  Copy to CD I have to reformat because I have no GUI interface and I need some files.   I can't load new system into new partition because it is too small.  HELP!!!
If you want to copy the files, cp is the command like this:
```
cp filename /path/to/destination
```
I suggest you read the man page for more specific information.

---

### Post by DirtDawg on 2006-10-04
Oops, I read the original post incorrectly. Sorry about that. 

Luckily, Azz saves the day *again*. Thanks Azz!

---

### Post by ardchoille on 2006-10-04
> **azz said:**
> [http://yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)

mkisofs -r -R -J -l -L /home/user1 | cdrecord dev=0,4,0 -v --eject speed=4 - 


I think you may have to use the dev=/dev/hdc (or whatever your burner is) syntax since 2.6 kernels do not use scsi emulation anymore....  And you don't have to use 4x speed, you can go as fast as your burner can go.  I think burnfree is on by default.

Hey! Thanks for that link :)

---

