---
title: "Window being dragged along"
date: 2016-11-01
forum: Desktop Environments
---

### Post by fbonnet08 on 2016-11-01
Hi, 

I just did an upgrade from 15.10 to 16.04 and for some reason when I switch from one workspace to another the window that I have the mouse pointer on gets dragged along to the next workspace.

I looked through unity and system settings under mouse and keyboard could not find how to stop dragging windows when I switch workspace! This is very annoying as it hands up shuffling all my windows around. 

How do I stop dragging windows around when I switch workspace?

---

### Post by Bucky Ball on 2016-11-01
Welcome. The upgrade went ok? 15.10 has been EOL for awhile so surprised it worked at all. Is this the only issue you are having? Or do you mean you did a clean install of 16.04 LTS from USB or disk?

Have you done an update/upgrade since you upgraded? Try this in a terminal and post any errors you get between code tags, please.
```

sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Reboot. This will NOT upgrade you to 16.10. ;)

If you're still having odd issues, please post this file here, between code tags, IF you did a net upgrade from 15.10 to 16.04 (though not sure how this is possible unless you went an unconventional route. Please confirm details of how you upgraded).

```
sudo nano /etc/apt/sources.list
```

[See the link in the first line of my signature at bottom of post for how to create code tags.]

---

### Post by fbonnet08 on 2016-11-01
Hi,

I am still getting the same effect after

sudo apt autoremove
sudo apt update
sudo apt full-upgrade
the window are being snatch along when I switch workspace.

I am attaching the /etc/apt/sources.list file:


# deb cdrom:[Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial main restricted
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-updates main restricted
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial universe
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial universe
deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-updates universe
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial multiverse
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial multiverse
deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-updates multiverse
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-backports main restricted universe multiverse
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-backports main restricted universe multiverse


deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-security main restricted
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-security main restricted
deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-security universe
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-security universe
deb [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-security multiverse
deb-src [http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/) xenial-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner

---

### Post by Bucky Ball on 2016-11-01
Code tags, please. I asked twice. If you don't know how, see instructions from the green link in the first line of my signature below.

Please re-read my first post and answer some of the questions. You do not say whether those commands I gave resulted in errors or anything else. Thanks.

---

### Post by fbonnet08 on 2016-11-01
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I am still getting the same effect after[/COLOR]

[COLOR=#000000]sudo apt autoremove[/COLOR]
[COLOR=#000000]sudo apt update[/COLOR]
[COLOR=#000000]sudo apt full-upgrade[/COLOR]
[COLOR=#000000]the window are being snatch along when I switch workspace.[/COLOR]

[COLOR=#000000]I am attaching the /etc/apt/sources.list file:[/COLOR]

```

[COLOR=#000000]# deb cdrom:[Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main restricted[/COLOR]


[COLOR=#000000]# See [/COLOR][http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes)[COLOR=#000000] for how to upgrade to[/COLOR]
[COLOR=#000000]# newer versions of the distribution.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial main restricted[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial main restricted[/COLOR]


[COLOR=#000000]## Major bug fix updates produced after the final release of the[/COLOR]
[COLOR=#000000]## distribution.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-updates main restricted[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-updates main restricted[/COLOR]


[COLOR=#000000]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu[/COLOR]
[COLOR=#000000]## team. Also, please note that software in universe WILL NOT receive any[/COLOR]
[COLOR=#000000]## review or updates from the Ubuntu security team.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial universe[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial universe[/COLOR]
[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-updates universe[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-updates universe[/COLOR]


[COLOR=#000000]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu [/COLOR]
[COLOR=#000000]## team, and may not be under a free licence. Please satisfy yourself as to [/COLOR]
[COLOR=#000000]## your rights to use the software. Also, please note that software in [/COLOR]
[COLOR=#000000]## multiverse WILL NOT receive any review or updates from the Ubuntu[/COLOR]
[COLOR=#000000]## security team.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial multiverse[/COLOR]
[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-updates multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-updates multiverse[/COLOR]


[COLOR=#000000]## N.B. software from this repository may not have been tested as[/COLOR]
[COLOR=#000000]## extensively as that contained in the main release, although it includes[/COLOR]
[COLOR=#000000]## newer versions of some applications which may provide useful features.[/COLOR]
[COLOR=#000000]## Also, please note that software in backports WILL NOT receive any review[/COLOR]
[COLOR=#000000]## or updates from the Ubuntu security team.[/COLOR]
[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-backports main restricted universe multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-backports main restricted universe multiverse[/COLOR]


[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-security main restricted[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-security main restricted[/COLOR]
[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-security universe[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-security universe[/COLOR]
[COLOR=#000000]deb [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-security multiverse[/COLOR]
[COLOR=#000000]deb-src [/COLOR][http://mirror.as24220.net/pub/ubuntu-archive/](http://mirror.as24220.net/pub/ubuntu-archive/)[COLOR=#000000] xenial-security multiverse[/COLOR]


[COLOR=#000000]## Uncomment the following two lines to add software from Canonical's[/COLOR]
[COLOR=#000000]## 'partner' repository.[/COLOR]
[COLOR=#000000]## This software is not part of Ubuntu, but is offered by Canonical and the[/COLOR]
[COLOR=#000000]## respective vendors as a service to Ubuntu users.[/COLOR]
[COLOR=#000000]# deb [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] utopic partner[/COLOR]
[COLOR=#000000]# deb-src [/COLOR][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)[COLOR=#000000] utopic partner[/COLOR]

```

---

### Post by CantankRus on 2016-11-01
Reset compiz to default.
In terminal ...
```
dconf reset -f /org/compiz/
```
Log out and back in.

---

### Post by fbonnet08 on 2016-11-01
Hi,

tried to reset the compiz the problem still persists the windows being dragged along when switching workspace.

I have created a new fresh account on the same machine with the same installation and the problem is not there, when I switch workspace the window does not get dragged along.

There must be a config file or a corrupted file or setting that I do not know about which is creating this behaviour.

---

### Post by fbonnet08 on 2016-11-01
Hi Bucky Ball,

to answer about the error after the commands run, apart from the chrome browser I see no errors:


sudo apt autoremove:


```

$ sudo apt autoremove
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  buteo-syncfw indicator-transfer indicator-transfer-buteo indicator-transfer-download-manager libbuteosyncfw5-0 libindicator-transfer0
  libiphb0
0 to upgrade, 0 to newly install, 7 to remove and 4 not to upgrade.
After this operation, 2,136 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 463020 files and directories currently installed.)
Removing buteo-syncfw (0.7.21+16.04.20151216.1-0ubuntu1) ...
Removing indicator-transfer-download-manager (0.2+16.04.20151216.5-0ubuntu1) ...
Removing indicator-transfer-buteo (0.1+15.10.20151006-0ubuntu1) ...
Removing indicator-transfer (0.2+16.04.20151216.5-0ubuntu1) ...
Removing libbuteosyncfw5-0:amd64 (0.7.21+16.04.20151216.1-0ubuntu1) ...
Removing libindicator-transfer0 (0.2+16.04.20151216.5-0ubuntu1) ...
Removing libiphb0:amd64 (1.2.4+15.10.20150929-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.48.1-1~ubuntu16.04.1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...

```


sudo apt update:


```

$ sudo apt update
Hit:1 http://mirror.as24220.net/pub/ubuntu-archive xenial InRelease
Hit:2 http://mirror.as24220.net/pub/ubuntu-archive xenial-updates InRelease
Get:3 http://mirror.as24220.net/pub/ubuntu-archive xenial-backports InRelease [92.2 kB]
Hit:4 http://mirror.as24220.net/pub/ubuntu-archive xenial-security InRelease        
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:6 http://dl.google.com/linux/chrome/deb stable Release
Fetched 92.2 kB in 1s (83.7 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/chrome/deb stable InRelease' doesn't support architecture 'i386'

```


sudo apt full-upgrade:


```

$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  address-book-service qtcontact5-galera
The following packages will be upgraded:
  base-files unattended-upgrades
2 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.
Need to get 99.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://mirror.as24220.net/pub/ubuntu-archive xenial-updates/main amd64 base-files amd64 9.4ubuntu4.3 [67.7 kB]
Get:2 http://mirror.as24220.net/pub/ubuntu-archive xenial-updates/main amd64 unattended-upgrades all 0.90ubuntu0.1 [31.7 kB]
Fetched 99.4 kB in 0s (2,512 kB/s)             
Preconfiguring packages ...
(Reading database ... 462982 files and directories currently installed.)
Preparing to unpack .../base-files_9.4ubuntu4.3_amd64.deb ...
Unpacking base-files (9.4ubuntu4.3) over (9.4ubuntu4.2) ...
Processing triggers for plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for cracklib-runtime (2.9.2-1build2) ...
Processing triggers for initramfs-tools (0.122ubuntu8.5) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-45-generic
Setting up base-files (9.4ubuntu4.3) ...
(Reading database ... 462982 files and directories currently installed.)
Preparing to unpack .../unattended-upgrades_0.90ubuntu0.1_all.deb ...
Unpacking unattended-upgrades (0.90ubuntu0.1) over (0.90) ...
Processing triggers for systemd (229-4ubuntu11) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.5-1) ...
Setting up unattended-upgrades (0.90ubuntu0.1) ...
Replacing config file /etc/apt/apt.conf.d/50unattended-upgrades with new version
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults

```

---

### Post by Bucky Ball on 2016-11-01
You have the i386 Ubuntu installed? You have this error.

```
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/chrome/deb stable InRelease' doesn't support architecture 'i386'
```

You should delete or disable this PPA and run those commands again. Might not have anything to do with your issue, but this is an issue.

```
http://dl.google.com/linux/chrome/deb stable
```

Software and Updates> Other Software> disable that PPA.

---

### Post by CantankRus on 2016-11-02
You could try removing all the dconf user settings.
This has to be done from a tty terminal after you logout else the file will be recreated.

Log out to the greeter.
Hit ctrl+alt+F1
Login and run...
```
mv ~/.config/dconf/user ~/.config/dconf/user.bak
```
Type in "exit" and then return to the greeter... ctrl+alt+F7 and log in to desktop.
You will need to enable workspaces in System Settings > Appearance > Behaviour


If no change, logout to the greeter again and repeat using this command
instead of previous one to move your user settings back.
```
mv ~/.config/dconf/user.bak ~/.config/dconf/user
```

---

### Post by fbonnet08 on 2016-11-03
Hi CantankRus,

ok that worked removing all the settings via /.config/dconf/user file removal.

No more crazy window shuffling! Thanks.

---

### Post by Bucky Ball on 2016-11-03
If solved, please mark as 'solved' using Thread Tools at top right of the page. It will not close the thread but will help others. Thanks.

---

### Post by fbonnet08 on 2016-11-04
Hi,

removing all of the 
[code]
rm ~/.config/dconfig/user*
[\code]
then logged out and/or reboot actually worked. Resets all of the settings but cures it.

---

### Post by CantankRus on 2016-11-04
> **fbonnet08 said:**
> Hi,

removing all of the 
[code]
rm ~/.config/dconfig/user*
[\code]
then logged out and/or reboot actually worked. Resets all of the settings but cures it.

Ok, good.
Bit overkill, but when it's difficult to see what's causing the problem, sometimes easiest.
Just means you have to redo all the little user settings you changed and hopefully you'll see what causes it as you go.

I would have thought it was a window manager (compiz) setting but resetting compiz had no effect.

---

