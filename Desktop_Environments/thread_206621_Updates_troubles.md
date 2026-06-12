---
title: "Updates troubles"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Matt Houston on 2006-06-30
Hey. 

Every time I try and install the updates on Dapper it tells me some packages have not been installed and to run sudo apt-get dist-upgrade in the terminal, which has the following result:

```
adrian@Adrian:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages have been kept back:
  gdk-imlib1 gnome-cups-manager python-netcdf
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
adrian@Adrian:~$

```

Any ideas?

---

### Post by invalid on 2006-06-30
[QUOTE=Matt Houston]Hey. 

Every time I try and install the updates on Dapper it tells me some packages have not been installed and to run sudo apt-get dist-upgrade in the terminal, which has the following result:

```
adrian@Adrian:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages have been kept back:
  gdk-imlib1 gnome-cups-manager python-netcdf
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
adrian@Adrian:~$

```

Any ideas?[/QUOTE]
Try doing
```
sudo apt-get install gdk-imlib1
sudo apt-get install gnome-cups-manager
sudo apt-get install python-netcdf

```

This should tell us what the problem is, or more information as to where to look.

---

### Post by Matt Houston on 2006-06-30
```
adrian@Adrian:~$ sudo apt-get install gdk-imlib
Password:
Reading package lists... Done
Building dependency tree... Done
Package gdk-imlib is a virtual package provided by:
  gdk-imlib11 1.9.14-29ubuntu1
You should explicitly select one to install.
E: Package gdk-imlib has no installation candidate
adrian@Adrian:~$

```

```
adrian@Adrian:~$ sudo apt-get install gnome-cups-manager
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgnomecupsui1.0-1c2a
The following packages will be REMOVED
  libgnomecupsui1.0-1
The following NEW packages will be installed
  libgnomecupsui1.0-1c2a
The following packages will be upgraded:
  gnome-cups-manager
1 upgraded, 1 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B/343kB of archives.
After unpacking 36.9kB disk space will be freed.
Do you want to continue [Y/n]?

```

Should I say yes? (I'm pretty useless at this)

```
adrian@Adrian:~$ sudo apt-get install python-netcdf
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libnetcdf3
Suggested packages:
  netcdf-doc
The following packages will be REMOVED
  netcdfg3
The following NEW packages will be installed
  libnetcdf3
The following packages will be upgraded:
  python-netcdf
1 upgraded, 1 newly installed, 1 to remove and 2 not upgraded.
Need to get 96.7kB of archives.
After unpacking 57.3kB disk space will be freed.
Do you want to continue [Y/n]?

```

And to this one?

---

### Post by shrift on 2006-06-30
It wouldn't warning you about those packages unless there was some sort of a conflict.

First try using aptitude to do the upgrades, it has a little more info. So launch aptitude "sudo aptitude"

then type "U" make sure you use the uppercase.

It will tell you if there are conflicts, and try to resolve them.

If that doesn't help, please post your /etc/apt/sources.list file here. You can view that with a "gedit /etc/apt/sources.list"

I am wondering if you have any funny repositories installed.


Either way, the fact that it is telling you that it won't install those files is no big deal. As long as your system is running fine, then it's nothing to worry about.

---

### Post by invalid on 2006-06-30
[QUOTE=Matt Houston]```
adrian@Adrian:~$ sudo apt-get install gdk-imlib
Password:
Reading package lists... Done
Building dependency tree... Done
Package gdk-imlib is a virtual package provided by:
  gdk-imlib11 1.9.14-29ubuntu1
You should explicitly select one to install.
E: Package gdk-imlib has no installation candidate
adrian@Adrian:~$

```
[/QUOTE]
```
sudo apt-get install gdk-imlib11
```
[QUOTE=Matt Houston]
```
adrian@Adrian:~$ sudo apt-get install gnome-cups-manager
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgnomecupsui1.0-1c2a
The following packages will be REMOVED
  libgnomecupsui1.0-1
The following NEW packages will be installed
  libgnomecupsui1.0-1c2a
The following packages will be upgraded:
  gnome-cups-manager
1 upgraded, 1 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B/343kB of archives.
After unpacking 36.9kB disk space will be freed.
Do you want to continue [Y/n]?

```

Should I say yes? (I'm pretty useless at this)
[/QUOTE]
Yes, it will replace some older packages with new updates

[QUOTE=Matt Houston]
```
adrian@Adrian:~$ sudo apt-get install python-netcdf
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libnetcdf3
Suggested packages:
  netcdf-doc
The following packages will be REMOVED
  netcdfg3
The following NEW packages will be installed
  libnetcdf3
The following packages will be upgraded:
  python-netcdf
1 upgraded, 1 newly installed, 1 to remove and 2 not upgraded.
Need to get 96.7kB of archives.
After unpacking 57.3kB disk space will be freed.
Do you want to continue [Y/n]?

```
And to this one?[/QUOTE]
Same as above, type yes.

---

### Post by Matt Houston on 2006-06-30
[QUOTE=invalid]Try doing
```
sudo apt-get install gdk-imlib1
sudo apt-get install gnome-cups-manager
sudo apt-get install python-netcdf

```

This should tell us what the problem is, or more information as to where to look.[/QUOTE]

Did the trick. Thanks for the help guys.

---

### Post by Matt Houston on 2006-07-01
OK, something went horribly wrong here. I think when I was playing around with apititude I deleted something I shouldn't have.

This morning when I booted up everything looked fine until I got the following:

```
Failed start X Server
It is likely it is not set up corectly. Would you like to view the X Server output to diagnose the problem?
```

To I which I say yes, and it gives me a load of information I really can't understand. What do you think? Is there anyway I can install Gnome again from the installation CD or from the command line?

The most worrying thing is when I boot from a live CD I can't see any of my files.

---

### Post by invalid on 2006-07-01
[QUOTE=Matt Houston]OK, something went horribly wrong here. I think when I was playing around with apititude I deleted something I shouldn't have.

This morning when I booted up everything looked fine until I got the following:

```
Failed start X Server
It is likely it is not set up corectly. Would you like to view the X Server output to diagnose the problem?
```
[/QUOTE]
Try reconfiguring the xserver with the following command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Matt Houston on 2006-07-01
Gave it a try but no dice, I think I have isolated the problem though with these errors:

-unable to find valid framebuffer device
-NV(0): failed to open framebuffer device
-Screen(s) found, but none have a usable configuration

Do you know which parts of the xserver configuration could fix these problems, there's a lot of settings.

---

### Post by Matt Houston on 2006-07-02
OK, forget fixing xserver, we've gone beyond that now. What really concerns me is my home directory was about 55 gigs, but when I boot using SLAX and calculate the space on the drive it says 32 megs!!!

Is there anyway this could be a mistake....is there anyway I can retrieve my data?

---

