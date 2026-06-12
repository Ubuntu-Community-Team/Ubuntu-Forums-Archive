---
title: "No gdm"
date: 2008-05-14
forum: Desktop Environments
---

### Post by darkreaction on 2008-05-14
Ok I am dumb. So I disabled graphical login manager (gdm) so now I don't have a graphical interface. I am using a live cd right now so I guess is there any way to re-enable gdm? thanks

---

### Post by MaindotC on 2008-05-14
You can start gdm, or Gnome Desktop Manager, by typing:
```

sudo gdm

```

In the /etc folder there are folders that correlate to something called [run-levels:]("http://en.wikipedia.org/wiki/Runlevel#Ubuntu")
```

311@a34lkj2348dsf311-laptop:~$ cd /etc/rc
rc0.d/ rc1.d/ rc2.d/ rc3.d/ rc4.d/ rc5.d/ rc6.d/ rcS.d/

```

This displays each folder for each run level.  If you go into each folder, there should files that start with a capital S.  The capital S means "start" in lamen's terms.  The operating system loads whatever processes are in this folder depedning on the run level at which you are logging in.  The wiki says Debian-based systems use run level 2 - 5 for graphical login.  When you change the captial S to something else, like a lowercase s or one convention is to name it with a K (for kill), the process is not started.

In one of those folders, there should be a process that ends in "gdm" but doesn't start with a capital S.  Change that to a capital S and restart your x-server by pressing ctrl + alt + backspace.

---

### Post by MaindotC on 2008-05-20
What's the status on this post? Have you made any progress?

---

### Post by atomkarinca on 2008-05-20
You can try

```
sudo dpkg-reconfigure gdm
```

if you have gdm installed. If you removed it just install it

```
sudo apt-get install gdm
```

and start it

```
sudo /etc/init.d/gdm start
```

---

