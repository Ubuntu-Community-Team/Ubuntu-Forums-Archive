---
title: "Something is broken - I think it's apt"
date: 2009-05-14
forum: General Help
---

### Post by dodle on 2009-05-14
I was following some instructions to remove the arrow from the gnome menu.

[http://ubuntuforums.org/showthread.php?t=733808](http://ubuntuforums.org/showthread.php?t=733808)

I had to stop in the middle of it to install sysinfo, which messed things up.  Now I cannot install anything.  This is the terminal outpus:> **dodle's terminal]:~$ sudo apt-get install sysinfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sysinfo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up apt-build (0.12.37) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing apt-build (--configure):
 subprocess post-installation script returned error exit status 1
Setting up postfix (2.5.5-1.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on postfix | mail-transport-agent said:**
> 

If I try "sudo dpkg-reconfigure apt":[quote=dodle's terminal]:~$ sudo dpkg-reconfigure apt
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable


---

### Post by KhurramM on 2009-05-14
From what I observe:

>  Originally Posted by dodle's terminal
:~$ sudo apt-get install sysinfo
Reading package lists... Done
Building dependency tree
Reading state information... Done
sysinfo is already the newest version.
.....
.....


Try to install something not installed and see the results.

---

### Post by Cl0ud9 on 2009-05-14
Try this:
```

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update

```

---

### Post by petrus4 on 2009-05-14
> **dodle said:**
> 
If I try "sudo dpkg-reconfigure apt":

Is synaptic running at the same time?  That can produce that error.

---

### Post by ad_267 on 2009-05-14
Check for a lock file or something in /var/cache/debconf and kill any dpkg, apt or similar processes.

Found this thread here: [http://linux.derkeiler.com/Mailing-Lists/Debian/2003-12/5763.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2003-12/5763.html)
So you might have to do a reboot.

Then do:
> sudo aptitude reinstall apt-build postfix bsd-mailx

---

### Post by dodle on 2009-05-14
I restarted my system which seems to have fixed the problem.  When I first booted back up, I tried to install something, then a dialog came up in the terminal asking for my processor.  I'm using an AMD Sempron, but it wasn't on the list so I just picked Athlon64 (hope that doesn't mess anything else up).  After that I uninstalled apt-build then did:

```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
```

Things seem to be working normal again.  Thanks for your help.

---

