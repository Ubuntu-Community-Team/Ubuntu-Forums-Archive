---
title: "Bootmrg missing?GRUB/boot help!"
date: 2009-04-27
forum: General Help
---

### Post by Questioneer on 2009-04-27
hello-
I recently installed ubuntu 9.04 next to my Windows 7 beta partition. 
Now,I can't boot the windows 7 partition.

Here's my condensed disk -l:
```

/dev/sda1   *      5    Extended
/dev/sda3          7    HPFS/NTFS
/dev/sda5          83   Linux
/dev/sda6          82   Linux swap/Solaris

```

Here's the boot code I'm currently using with GRUB:
```

title Windows 7
root (hd0,2)
chainloader +1

```

But when I try to boot windows 7, I get
```
Bootmrg missing
```

What should I do???

NOTE: I have tried multiple times to put in my windows 7 beta CD, and click "repair system", but my windows 7 operating system does not show up in the list, so I cannot repair the problem using the windows 7 cd.

The only thing I can think of is the beta may have expired, and the CD is coded to not repair expired betas.

NOTE: Using the command prompt on the cd to repair the bootmrg also does not work. 

NOTE: I am thinking of using the ms-sys program, but this doesn't come with Jaunty! How can I install it?(Please, if you tell me to install it from source, provide instructions. Every program I've ever tried to install from source hasn't worked properly when following the readme.)

Thanks,
Questioneer

---

### Post by Questioneer on 2009-04-27
great. I installed the ms-sys program, and followed this tutorial to try and fix my mbr, and now when I boot I just get a blinking underscore.(no grub or anything) 
Now I can't boot into Windows or Ubuntu.

PS- trying "fixmbr" with my recovery CD doesn't work. It says it isn't a valid command.

---

### Post by Questioneer on 2009-04-27
Here's the tutorial I tried to use:
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

ms-sys said that the MBR was installed correctly on sda, but apparently it wasn't.

---

