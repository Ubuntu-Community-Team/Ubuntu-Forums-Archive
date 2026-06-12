---
title: "Memory Out of 1 Mb"
date: 2009-06-19
forum: General Help
---

### Post by vishalag on 2009-06-19
Hi everyone,

This is a strange problem I am facing on Ubuntu. I am compiling a program which has got something to write in "/tmp" folder. Now I have 350 Mb space left on device but it says that no space left on device. When I check the properties of /tmp folder, I find that it says 636 kB free "out of 1 Mb". Can anyone say what does it mean?

How I can I increase its size or why does it not the hard disk itself?

Thanks in advance

Vishal

---

### Post by vishalag on 2009-06-19
Has noone faced a similar thing ???????

---

### Post by mali2297 on 2009-06-19
Check if another filesystem is mounted on /tmp. You can use the command
```

sudo mount -l

```

I have /tmp mounted as tmpfs, so I get the output
```

/tmp on /tmp type tmpfs (rw)

```
If you also have it mounted as tmpfs, then you might want to change the mount options in /etc/fstab to allow greater memory or just not mounting tmpfs at all. You can read about tmpfs at [http://www.ibm.com/developerworks/library/l-fs3.html](http://www.ibm.com/developerworks/library/l-fs3.html) and [http://en.wikipedia.org/wiki/TMPFS](http://en.wikipedia.org/wiki/TMPFS).

---

### Post by vishalag on 2009-06-19
there is no file like /etc/fstab????

And yes I have it mounted on my tmp.

mount -l also gives an error of "overflow on /tmp .. (rw,size=1mb,mode=1777)"

---

### Post by mali2297 on 2009-06-19
> **vishalag said:**
> there is no file like /etc/fstab????

Are you sure? I don't use Ubuntu anymore but I think /etc/fstab is pretty much standard for all Linux distros. Try opening it with
```

sudo nano -Bw /etc/fstab

```

---

### Post by vishalag on 2009-06-19
Thanks for a reply 

Yeah , i checked that thouroughly. Even there is no file like that in my whole ubuntu.

Is mode=1777 right? Because I remember that some days ago I set that value to 1777 somewhere.[ I am sorry I play with ubuntu so much that I dont remember where I did it.]

Best regards
Vishal

---

### Post by mali2297 on 2009-06-19
Do you have a file /etc/mtab? If so, you can use it as a template for creating /etc/fstab.

You are not using Wubi, are you? (That is, running Ubuntu inside Windows.)

---

### Post by geirha on 2009-06-19
During boot, the disk usage of / is checked, and if it is full, it mounts 1 MB of ram to /tmp so that the programs needed to complete the boot will have at least a little bit of temporary space to use (otherwise they will fail, and you won't be able to boot at all). Once you've freed up some space on /, you can run 
```
sudo /etc/init.d/mountoverflowtmp stop
``` to unmount the ramdisk. Rebooting will have the same effect.

---

