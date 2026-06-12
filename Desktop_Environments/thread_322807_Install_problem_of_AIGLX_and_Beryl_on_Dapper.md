---
title: "Install problem of AIGLX and Beryl on Dapper"
date: 2006-12-21
forum: Desktop Environments
---

### Post by ramjet_1953 on 2006-12-21
Hi Guys!

I'm trying to install AIGLX and Beryl on my Acer TravelMate 4101.
It has the Intel 915 Graphics chipset.

I have the 2.6.15-27.50 kernel (686) 
I am using Dapper (6.06 LTS)

I'm using the Dapper guide from the Beryl Wiki and get as far as this command:

sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname` -r

I get the following error:

roger@roger-laptop:~$ sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules- `uname -r`
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-dri-modules
roger@roger-laptop:~$

Is there a problem with using the 686 kernel, or am I doing something wrong?

Regards,
Roger 8)

---

### Post by ramjet_1953 on 2006-12-21
As an addendum to the above, I get the following, when I do a:

sudo apt-get update

Fetched 5944B in 18s (320B/s)
Failed to fetch [http://ubuntu.beryl-project.org/dists/dapper/Release](http://ubuntu.beryl-project.org/dists/dapper/Release)  Unable to find expected entry  aiglx/binary-i386/Packages in Meta-index file (malformed Re lease file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.

Regards,
Roger 8)

---

### Post by alek01 on 2007-01-01
Hi Ramjet,
I'm at the same stage as you on instally Beryl. Did you ever solve the problem? I've tried everything I can think of. Noway to get the packages.
Thanks for your help.
Happy new Year.
Alek

---

### Post by t1m on 2007-01-11
Hmm if you go to [http://ubuntu.beryl-project.org/dists/dapper/main/]("http://ubuntu.beryl-project.org/dists/dapper/main/") you can see some of the packages.... but if you try to install them via apt-get it doesn't work. :(

*bump*

T1m

---

