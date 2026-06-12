---
title: "Quake 4 installation problems"
date: 2006-09-21
forum: Gaming &amp; Leisure
---

### Post by lckeeper1 on 2006-09-21
Hey all,

I just picked up a copy of Quake 4, except I can't seem to install it at all. When I place the first disk in the drive, everything pops up fine, and I have full permissions to do whatever I like.

The problem starts when I put in the second disk. I get an error message that I don't have permission to view the files. Ok, I can deal with that. Then I try to copy the files from the terminal with the following command using sudo and I get the following results:

```
sudo cp /media/cdrom/Setup/Data/q4base/* /home/ubuntu/games/quake4/q4base/
cp: cannot stat `/media/cdrom/Setup/Data/q4base/*': No such file or directory
```


I'm not exactly sure what to do to gain access to the additional .pak files. I'm also confused as to how the first disk has no problems, yet the others do.

Any help for this Linux noob would be much appreciated. Thanks in advance.

---

### Post by lckeeper1 on 2006-09-22
Quick update. I copied the files from my windows partition, and I downloaded the most up-to-date installer from the id software. I cd to the directory where the installer is, but when I run the install command, I get the following output:
```

ubuntu@ubuntu-desktop:/usr/local/games/quake4$ sudo sh quake4-linux-1.3.-2.x86.run
sh: quake4-linux-1.3.-2.x86.run: No such file or directory
```

The only thing is I know for a fact the file is right there. I can see it in nautilus.

I'm looking foward to playing a great game under a great OS, so any help would be appreciated, as I'm stuck. Thanks!

---

### Post by oskarloko on 2006-09-24
```

sudo sh **./**quake4-linux-1.3.-2.x86.run

```

If you type
*$ myexec*
you say shell to execute the first *myexec* executable file which is in yout path

then, if you type
*$ ./myexec *
you order the execution of the file *myexec* which is under actual directory.

---

