---
title: "Monitoring UPS"
date: 2005-08-17
forum: Desktop Environments
---

### Post by gaatmx on 2005-08-17
I have a Powerware 5115 and could not install the provided (propietary) software named LanSafe 5. 
The Linux installer simply fails every time. ](*,) 
Has anyone managed to install it?
If no,  [-X 
Has anyone managed to install and setup any of the open/free alternatives like 'nut'?
I know nut is on the repos but is seems outdated. :???: 
G.

---

### Post by aguy on 2006-07-11
Hi,

I have just managed to install Lansafe 5 on Ubuntu Breezy Badger.  It is now working successfully though it has taken me 2 days to get it working.  It is fairly simple to do if anyone is interested in how just let me know and I can give you instructions.

---

### Post by moopere on 2006-07-11
> **aguy said:**
> Hi,

I have just managed to install Lansafe 5 on Ubuntu Breezy Badger.  It is now working successfully though it has taken me 2 days to get it working.  It is fairly simple to do if anyone is interested in how just let me know and I can give you instructions.

Why not write up a HOWTO or even reply here - then other users will be able to find your instructions when they do a search.

Cheers,
Craig

---

### Post by gready on 2006-07-25
I am having trouble installing as well.

At first the install failed say boggus - I have worked that out and fixed by editing the install script file and removing the '-' that is infront of the 'ps -ax' command so it reads 'ps ax'.

But now when the install get to running install.ls I get this

./install.sh: line 2161:  5389 Segmentation fault      ./install.ls
/usr/lansafe/Bin/PowerMonitor.sh: line 19: ./PowerMonitor: No such file or directory

---

### Post by gready on 2006-07-25
OK I have managed to get Lansafe 4 installed and working but would still like to know why lansafe 5 dosen't work

---

### Post by martnemma on 2007-06-02
I also have a powerware 5115 how the hell do you get the software installed ? 

I have given up cant find/create directories etc.. 

What a PAIN in the head this is turning out to be !!


PLEASE PLEASE PLEASE can someone out their write a HOWTO !!


Thanks.

---

### Post by Tyler Oderkirk on 2007-07-28
This Gentoo HOWTO for the free UPS monitoring package called "NUT" might help you guys: [http://gentoo-wiki.com/HOWTO_NUT]("http://gentoo-wiki.com/HOWTO_NUT")

I haven't tried it yet.

-Tyler

---

### Post by ikt on 2008-05-25
> **Tyler Oderkirk said:**
> This Gentoo HOWTO for the free UPS monitoring package called "NUT" might help you guys: [http://gentoo-wiki.com/HOWTO_NUT]("http://gentoo-wiki.com/HOWTO_NUT")

I haven't tried it yet.

-Tyler

I will try this, after trying to get lansafe v5 installed I went about eventually downloading it from the website (was trying to install from cd) and noticed a file which explains:

Red Hat 7.2, 8.0, 9.0
Red Hat Enterprise Linux 3 and 4 (ES and AS)                                                 1Red Hat Enterprise Linux 4 (ES, AS, and Desktop)                                            2Red Hat Enterprise Linux AS v. 2.1 and v. 3               1
Fedora Core 5

are the only supported linux oss

Basically debian and its like aren't supported, which would explain why the installer fails.

Even when trying to install from tar it still hits:

```
Linking /etc/init.d/rc5.d/S89ls.init to /etc/init.d/ls.init ... ln: creating symbolic link `/etc/init.d/rc5.d/S89ls.init' to `/etc/init.d/ls.init': No such file or directory
Linking /etc/init.d/rc0.d/K89ls.init to /etc/init.d/ls.init ... ln: creating symbolic link `/etc/init.d/rc0.d/K89ls.init' to `/etc/init.d/ls.init': No such file or directory
Install failed. Exiting
```

:(

---

