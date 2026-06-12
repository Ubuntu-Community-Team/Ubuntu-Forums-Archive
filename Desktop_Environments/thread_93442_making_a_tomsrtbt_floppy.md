---
title: "making a tomsrtbt floppy"
date: 2005-11-22
forum: Desktop Environments
---

### Post by meldra on 2005-11-22
Greetings,

I guess this is where I should post this, as it doesnt seem to fit anywhere else.

I am trying to make a tomsrtbt floppy so that I can try install DSL properly on an ancient laptop via pcmcia, rather than piggyback the hdd onto another computer, which the past three times has only ended up in xserver not working at all due to extreme differences in hardware.

Anyway, my situation is that i have an IDE FDD, which doesnt automatically mount in Ubuntu (breezy 5.10, or the prior hoary install either). I have to mount it manually. Now tomsrtbt has an install script... but the install script doesnt recognise the path to my FDD or something. I dont know if this is an ubuntu issue, an issue with how i mount the FDD, or the FDD itself... Has anyone successfully made the tomsrtbt floppy under Ubuntu?

```
root@scorpion:~/Desktop/tomsrtbt-2.0.103# sudo mount -t msdos /dev/fd0 /media/floppy
root@scorpion:~/Desktop/tomsrtbt-2.0.103# ./install.s 
Don't forget to READ the FAQ.

Insert a blank writable 3.5" floppy diskette then strike ENTER.

About to fdformat /dev/fd0u1722
/dev/fd0u1722: Device or resource busy
 FAILED fdformat error Enter to continue...

root@scorpion:~/Desktop/tomsrtbt-2.0.103#
```

I've included in the code box, exactly what i do and what happens.

If anyone can help me with this, i'll be extremely grateful.

Meldra.

---

### Post by Iandefor on 2005-11-22
> Greetings,

I guess this is where I should post this, as it doesnt seem to fit anywhere else. 
This is the forum for general discussion. I think the forum that you want is Hardware Help. However, I'll take a stab at answering your question.
I'll make the assumption that /dev/fd0u1722 is defining a different block device than /dev/fd0 which is where you mounted the floppy disk. It looks like the install script believes the block device for your floppy drive is /dev/fd0u1722 even it's /dev/fd0. Going into the script and changing that might help (My advice would be to make a copy and make the change there, then run the copy)

EDIT: It actually looks like your problem is part of the package fdformat and not of Ubuntu itself. I don't know how much this will help, but I find that getting the manual page can be a good starting point. Here's an online version of the fdformat manual page: [man fdformat]("http://www.ss64.com/bash/fdformat.html")

---

### Post by meldra on 2005-11-22
Ok, I'm still stuck with this. I cannot seem to figure out what exactly I need to do.

If a mod thinks that this question would be better dealt in the hardware forum, and fits said forum, then by all means I invite you to move it there, i'd just rather not double-post.

---

### Post by meldra on 2005-11-22
Ok, I finally got the tomsrtbt disk made. The disk didnt work properly, but I dont know if that was the disk or the drive. 

To make the FDD capable of making a 1.722 mb disk, you need to first run this command:

> superformat /dev/fd0 sect=21 cyl=83

<insert edit here>

I hope this might help someone in the future. I am not yet sure if this command would need to be redone after a reboot or not, so it might not be a permanent thing.

edit: This formatted the floppy currently in the FDD to the 1.722 format. However, I was able to re-run the tomsrtbt script again without having to redo this command.

---

