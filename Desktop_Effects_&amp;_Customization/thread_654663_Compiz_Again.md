---
title: "Compiz Again"
date: 2007-12-31
forum: Desktop Effects &amp; Customization
---

### Post by YSA.mak on 2007-12-31
Hi,
Happy new year for all!
I tried to get the 3D efefcts working, but did not manage, under Gusty 7.10.
First :NO COMPOSITE ext, got it sorted by modifying the xconfig from composite "0" to Composite "Enable".
But still having message : advanced effects not available!
Help please

---

### Post by Ub1476 on 2007-12-31
Hi and happy new year!

The composite extension message is probably due to that you're using an ATI card with restricted drivers.

If that's right, edit your xorg.conf to "composite: 0" and install XGL.

```
sudo apt-get install xserver-xgl
```

Logout and login and try to enable it again.

---

### Post by family on 2007-12-31
```

family@Manual:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for family:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071231131514
family@Manual:~$ sudo apt-get remove xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xgl
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 4510kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 106556 files and directories currently installed.)
Removing xserver-xgl ...
family@Manual:~$ sudo apt-get install  xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1737kB of archives.
After unpacking 4510kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  xserver-xgl
Install these packages without verification [y/N]? y
Get:1 http://it.archive.ubuntu.com gutsy/universe xserver-xgl 1:1.1.99.1~git20070727-0ubuntu3 [1737kB]
Fetched 1737kB in 19s (91.1kB/s)                                               
Selecting previously deselected package xserver-xgl.
(Reading database ... 106538 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20070727-0ubuntu3_i386.deb) ...
Setting up xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3) ...

family@Manual:~$ sudo apt-get install compiz compiz-core compizconfig-settings-manager compiz-gnome compiz-plugins compiz-fusion-plugins-main gnome-compiz-manager libcm7 libcompizconfig0 python-compizconfig
family@Manual:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


```
Extremely frustrating considering that compiz-fusion was working without a flaw a week ago (and I have made NO hardware changes!)...
Any help? I've had the xserver-xgl thing tossed at me a lot, but it doesn't help.

---

### Post by Forlong on 2007-12-31
Post your sources.list, there seems to something wrong:
```
cat /etc/apt/sources.list
```

---

### Post by family on 2007-12-31
I don't think there's anything wrong... It's extended, but lots of people use them;
[http://ubuntuforums.org/showthread.php?t=634099](http://ubuntuforums.org/showthread.php?t=634099)

---

### Post by family on 2007-12-31
Woah.. omg.
I rebooted after the xserver-xgl tangent and everything was in a lagggg. I enabled compiz using the skip_checks=yes line and the lag remained around the same. The cube was there. Caps were too, and a couple effects...
The horrendous lagggg of it astounded me though, so I switched back to metacity. But that lag remained.
What should I do? I know I can run these graphics perfectly under normal circumstances, but seeing as I'm coming from a clean install...

---

