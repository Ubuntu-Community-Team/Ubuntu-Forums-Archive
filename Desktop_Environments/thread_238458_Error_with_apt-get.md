---
title: "Error with apt-get"
date: 2006-08-17
forum: Desktop Environments
---

### Post by tristure on 2006-08-17
Hi,

I have problems with apt-get. There seem to be a problematic package (taskjuggler not to name it) that causes a persistent error.

I can't reinstall or remove it. And I get errors each time I install or remove other packages.

Here's a sample output (I don't know how to interprete it).

> tristan@tristan-desktop:~$ sudo apt-get install taskjuggler
Reading package lists... Done
Building dependency tree... Done
taskjuggler is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/1179kB of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "fr_FR:fr",
        LC_ALL = (unset),
        LANG = "fr_FR"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package taskjuggler.
(Reading database ... 83897 files and directories currently installed.)
Preparing to replace taskjuggler 2.2.0-1ubuntu1 (using .../taskjuggler_2.2.0-1ubuntu1_i386.deb) ...
Unpacking replacement taskjuggler ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
touch: missing file operand
Try `touch --help' for more information.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any help appreciated, I have absolutely no idea how to solve it.

---

### Post by -ko- on 2006-08-17
You can try the following thing:

```

sudo apt-get -f install 

```

This way, ubuntu will fix al dependencies problems, and maybe it will fix your problems to.

If this doesn't work, you can try to delete all the .deb files in /usr/bin /dpkg that have any association with taskjuggler.

---

### Post by tristure on 2006-08-18
Well I tried both and none of it works. It downloads the .deb again and then gives an error...

Any further idea welcome!

---

### Post by renota on 2007-02-11
In order to remove taskjuggler you have to install a good working version and then remove it.  
1) Find and download a newer version than the one you have installed.
[http://mirror.linux.org.mt/mirror/ubuntu/pool/universe/t/taskjuggler/taskjuggler_2.3.0-1_amd64.deb](http://mirror.linux.org.mt/mirror/ubuntu/pool/universe/t/taskjuggler/taskjuggler_2.3.0-1_amd64.deb)
2) Force install the new package, even if it has dependency errors:
dpkg -i --force-all taskjuggler_2.3.0-1_amd64.deb
3) Then remove it:
dpkg -r taskjuggler

Then get yourself a better package manager like synaptic because Adept is horrible.

---

### Post by pstep9407 on 2007-02-27
I have the same problem, and excuse me for being skeptical, but if taskjuggler has a problem, then forcing a newer package of broken software doesn't intuitively sound like a good idea. Can you provide some more info on why you think this is a good solution? 

I've included the transcript below. Only postgresql has given me these kinds of fits in the past on ubuntu. 


```
stephens@mackenzie:~$ sudo apt-get install konqueror
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  kcontrol kdebase-bin kdebase-data kdebase-kio-plugins kdesktop kfind kicker
  libdbus-qt-1-1c2 libkonq4
Suggested packages:
  mtools kicker-applets menu konq-plugins konq-speaker
Recommended packages:
  kamera kdemultimedia-kio-plugins
The following NEW packages will be installed:
  kcontrol kdebase-bin kdebase-data kdebase-kio-plugins kdesktop kfind kicker
  konqueror libdbus-qt-1-1c2 libkonq4
0 upgraded, 10 newly installed, 0 to remove and 64 not upgraded.
1 not fully installed or removed.
Need to get 22.2MB of archives.
After unpacking 48.8MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://archive.ubuntu.com dapper/universe taskjuggler 2.2.0-1ubuntu1 [1179kB]
Get:2 http://security.ubuntu.com dapper-security/main libkonq4 4:3.5.2-0ubuntu27 [258kB]
Get:3 http://security.ubuntu.com dapper-security/main kdebase-data 4:3.5.2-0ubuntu27 [5770kB]
Get:4 http://security.ubuntu.com dapper-security/main kicker 4:3.5.2-0ubuntu27 [1900kB]
Get:5 http://security.ubuntu.com dapper-security/main kcontrol 4:3.5.2-0ubuntu27 [7966kB]
Get:6 http://security.ubuntu.com dapper-security/main kdebase-bin 4:3.5.2-0ubuntu27 [1062kB]
Get:7 http://security.ubuntu.com dapper-security/main libdbus-qt-1-1c2 0.60-6ubuntu8.1 [172kB]
Get:8 http://security.ubuntu.com dapper-security/main kdebase-kio-plugins 4:3.5.2-0ubuntu27 [983kB]
Get:9 http://security.ubuntu.com dapper-security/main kdesktop 4:3.5.2-0ubuntu27 [758kB]
Get:10 http://security.ubuntu.com dapper-security/main kfind 4:3.5.2-0ubuntu27 [197kB]
Get:11 http://security.ubuntu.com dapper-security/main konqueror 4:3.5.2-0ubuntu27 [1957kB]
Fetched 22.2MB in 3m20s (111kB/s)
DESTROY created new reference to dead object ' Qt::SpacerItem', <> line 11 during global destruction.
(Reading database ... 147951 files and directories currently installed.)
Preparing to replace taskjuggler 2.2.0-1ubuntu1 (using .../taskjuggler_2.2.0-1ubuntu1_i386.deb) ...
Unpacking replacement taskjuggler ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
touch: missing file operand
Try `touch --help' for more information.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Selecting previously deselected package libkonq4.
Unpacking libkonq4 (from .../libkonq4_4%3a3.5.2-0ubuntu27_i386.deb) ...
Selecting previously deselected package kdebase-data.
Unpacking kdebase-data (from .../kdebase-data_4%3a3.5.2-0ubuntu27_all.deb) ...
Selecting previously deselected package kicker.
Unpacking kicker (from .../kicker_4%3a3.5.2-0ubuntu27_i386.deb) ...
Selecting previously deselected package kcontrol.
Unpacking kcontrol (from .../kcontrol_4%3a3.5.2-0ubuntu27_i386.deb) ...
Selecting previously deselected package kdebase-bin.
Unpacking kdebase-bin (from .../kdebase-bin_4%3a3.5.2-0ubuntu27_i386.deb) ...
Selecting previously deselected package libdbus-qt-1-1c2.
Unpacking libdbus-qt-1-1c2 (from .../libdbus-qt-1-1c2_0.60-6ubuntu8.1_i386.deb) ...
Selecting previously deselected package kdebase-kio-plugins.
Unpacking kdebase-kio-plugins (from .../kdebase-kio-plugins_4%3a3.5.2-0ubuntu27_i386.deb) ...
Selecting previously deselected package kdesktop.
Unpacking kdesktop (from .../kdesktop_4%3a3.5.2-0ubuntu27_i386.deb) ...
Selecting previously deselected package kfind.
Unpacking kfind (from .../kfind_4%3a3.5.2-0ubuntu27_i386.deb) ...
Selecting previously deselected package konqueror.
Unpacking konqueror (from .../konqueror_4%3a3.5.2-0ubuntu27_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/taskjuggler_2.2.0-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


stephens@mackenzie:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
stephens@mackenzie:~$ sudo dpkg --configure -a
Setting up kdebase-data (3.5.2-0ubuntu27) ...

Setting up kdebase-bin (3.5.2-0ubuntu27) ...

Setting up libkonq4 (3.5.2-0ubuntu27) ...

Setting up libdbus-qt-1-1c2 (0.60-6ubuntu8.1) ...

Setting up kfind (3.5.2-0ubuntu27) ...

Setting up kdesktop (3.5.2-0ubuntu27) ...

Setting up kdebase-kio-plugins (3.5.2-0ubuntu27) ...

Setting up kicker (3.5.2-0ubuntu27) ...

Setting up kcontrol (3.5.2-0ubuntu27) ...

Setting up konqueror (3.5.2-0ubuntu27) ...

stephens@mackenzie:~$

```

---

