---
title: "Problem with package manager and samba"
date: 2006-07-12
forum: Desktop Environments
---

### Post by bepe86 on 2006-07-12
Hi,

sorry, this has probably been asked for a few dozens time already, but I've been experiencing some problem with package installation lately, and samba is the naught one behind it all.

> sudo apt-get install -f -y
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 154456 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


This started happening after a recent security update, and I'm no guru, so i have no clue how to fix it. I see thatit's mentioning symlinks, what does "dangling" mean?

I get an error, even when i try to fix it using dpkg, apt, or  synaptic (which is logical, since they're all connected).

So, anyways, would be nice with a solution, right now, I can't reinstall the system, DVD-rom is broken, and I need to get a new one (it's for my laptop).

Thanks,

-bepe86

Edit:

nevermind, I manage to fix it, thanks to [http://ubuntuforums.org/showthread.php?t=190613](http://ubuntuforums.org/showthread.php?t=190613), simply

sudo rm /etc/rc3.d/K09samba
sudo rm /etc/rc2.d/K09samba
apt-get install -f

:)

---

### Post by celem on 2006-07-12
I am having the same problem. A bunch of updates were successful but samba's update fails. I too have tried various ways to reload, retry, fix, all to no avail.

---

### Post by s_g_robertson on 2006-07-13
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=214444]("http://ubuntuforums.org/showthread.php?t=214444")

Hope it is of some help.

Cheers.
Stephen

---

### Post by celem on 2006-07-13
Thanks Stephen,

It fixed it for me. I appreciate your help.

Ed

---

