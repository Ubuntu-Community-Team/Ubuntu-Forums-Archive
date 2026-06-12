---
title: "Suddenly, there is no disk space left on the file systm. Help"
date: 2009-03-28
forum: General Help
---

### Post by nathandyer on 2009-03-28
I was using Open Office when suddenly it posted that there wasn't enough disk space to continue working. I can't save anytime, programs randomly close, and the File Browser says that I have 0 bytes left of free space in the file system. Please help!

---

### Post by kanikilu on 2009-03-28
If you are truly out of space, I would recommend at least running ```
sudo apt-get clean
``` which will clear out the local repository of retrieved package files. It probably won't free up a ton of space, but might give you enough breathing room to use other tools to investigate and find other things to clean up.

You might also want to run ```
df /
``` to verify your free disk space is indeed that low...

I would use baobab or filelight to get a graphical representation of where your disk usage is. From there, it's pretty much on you to figure out what can safely be removed.

Out of curiosity, how are your partitions setup? You can do ```
sudo fdisk -l
``` or gparted to take a look.

Also, do you by any chance use a virtualization with VirtualBox or VMWare? The snapshots from those can eat up disk space quickly...

---

### Post by jkd18 on 2009-03-29
Thanks so olved my prmuch! Solved my problem TOO...!

---

### Post by AmericanPrincess109 on 2009-05-07
What did u do to fix this problem? I'm having the same problem and it's killing me. Please help me.
Thanks

---

### Post by cariboo on 2009-05-08
Open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

this will remove archived package from /var/cache/apt/archives. Next in the same terminal type:

```
sudo apt-get autoremove
```

This will remove any unneeded dependencies.

---

### Post by zob on 2009-05-17
Just had the same problem. When I managed to free up some space, my evolution profile (which had left me together with my firefox profile during the no space left-crisis), did come back.
So I had to create my accounts all over again to get them back. It took me some time, though I don't think anything was lost.

I remember the good old days with windows (well not exactly). But windows would warn you, when you got close to running out of space. It might be worth considering bringing a similar function to ubuntu.

---

### Post by irregardlessly on 2009-05-17
I'm surprised people are running that close on space these days with hard drives so cheap.

One time I tried to copy about 10 gigs of music at once to my ipod with gtkPod.  Well, it crashed halfway through and left a 5 gig temp file on my disk that took up all my free space and crashed some other stuff.  Probably not what any of you are encountering though.  :)

---

### Post by zob on 2009-05-18
Well irregardlessly, though it is not my case, remember that ubuntu is a free OS translated to many languages. The possibility exits that someone outside Pennsylvania, maybe even outside the states or the industrialized world, is going to use it. In that light, if not for any other reason, it could be nice if ubuntu had a warning system.

The fact that I'm just a jerk that is running ubuntu on a partition on an old PC, when I could have bought a new hard drive, doesn't change the fact that someone might actually not have the possibility of upgrading their hardware.

My situation occurred during a badly written command for rsync, which had my backup end up in my file system instead of on an external drive (which I do have).

---

### Post by jms1989 on 2009-05-18
I had a similar problem on my home server with its 11GB root partition filling up. It's logs had mysteriously grew very large, the kern.log, syslog, and debug grew by a few gigabytes causing other programs to spit out errors about not being able to write anything.

I had to login to the machine physically to login and remove the pesky files, once done, everything functioned normally.

So, I suggest looking in your /var/log/ directory for any files over 100MB. You'll need to use sudo to delete them.

---

