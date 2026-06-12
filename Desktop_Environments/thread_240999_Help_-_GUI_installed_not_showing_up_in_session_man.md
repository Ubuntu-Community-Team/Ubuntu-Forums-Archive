---
title: "Help - GUI installed not showing up in session manager?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by Dark Damo on 2006-08-21
Hey guys i installed a GUI from source called "AfterStep" and it successfully installed. BUT - It wont show up in session manager.

Here is the URL for the siteL

[http://www.afterstep.org/](http://www.afterstep.org/)

I need some help. Thanks.

---

### Post by Fass on 2006-08-21
Create a file called afterstep.desktop in /usr/share/xsessions/

```
gksudo gedit /usr/share/xsessions/afterstep.desktop
```

Insert the following into it:
```
[Desktop Entry]
Encoding=UTF-8
Name=Afterstep
Comment=This logs you into Afterstep
Exec=afterstep
Icon=
Type=Application
```

Then do:

```
sudo chmod 755 /usr/share/xsessions/afterstep.desktop
```

I'm not sure of that last step is necessary, but this should do the trick.

---

### Post by Dark Damo on 2006-08-22
I ended up getting "afterstep couldnt not be found" or something like that. Do i put that last line in the gedit thing?

Thanks

---

### Post by mcduck on 2006-08-22
Of course Afterstep is also available in Ubuntu repositories, so instead of compiling it from source you could have just run 'sudo apt-get install afterstep' ;)

---

### Post by Dark Damo on 2006-08-22
```
damo@damo-desktop:~/Desktop/Fluxbox/fluxbox-1.0rc2$ sudo apt-get install afterstep
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package afterstep

```

Hmm i keep getting that when i try. Am i doing something wrong?

---

### Post by mcduck on 2006-08-22
> **Dark Damo said:**
> ```
damo@damo-desktop:~/Desktop/Fluxbox/fluxbox-1.0rc2$ sudo apt-get install afterstep
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package afterstep

```

Hmm i keep getting that when i try. Am i doing something wrong?

Have you enabled Universe & Multiverse repositories? I bet Afterstep is in Universe.

[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")

---

### Post by Dark Damo on 2006-08-22
Will try now. Thanks.

---

### Post by Dark Damo on 2006-08-22
I got a few errors adding that stuff in lke 404s and some stuff about AMD64.

But Afterstep is downloading now. Thanks.

BTW im using Ubuntu 6.06. Is there those repositry things for that? because i used the 5.10 ones.

---

### Post by mcduck on 2006-08-22
Damn. I didn't even notice that that lins still has Breezy's repos.

They are pretty much same, but replace every 'breezy' with 'dapper'. You shouldn't use breezy's repositories with Dapper, the stuff is too outdated.

Or make yourself a nice new sources.list with [Source-O-Matic]("http://www.ubuntulinux.nl/source-o-matic") :D

---

### Post by Dark Damo on 2006-08-22
I got this error:

```
amo@damo-desktop:~$ sudo apt-get install afterstep
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  imagemagick libafterimage0 libafterstep1 libltdl3 libmagick6 libungif4g menu
Suggested packages:
  wmavgload asload wmcpuload asmon wmtop asmail asclock wmitime mc bitchx
  html2ps libwmf-bin
The following NEW packages will be installed:
  afterstep imagemagick libafterimage0 libafterstep1 libltdl3 libmagick6
  libungif4g menu
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 6592kB of archives.
After unpacking 18.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com breezy/main libltdl3 1.5.6-6 [154kB]
Get:2 http://archive.ubuntu.com breezy/universe menu 2.1.25 [426kB]
Get:3 http://security.ubuntu.com breezy-security/main libmagick6 6:6.2.3.4-1ubuntu1.2 [1320kB]
Get:4 http://security.ubuntu.com breezy-security/main imagemagick 6:6.2.3.4-1ubuntu1.2 [1334kB]
Get:5 http://archive.ubuntu.com breezy/universe libafterimage0 2.1.1-2ubuntu2 [264kB]
Get:6 http://archive.ubuntu.com breezy/universe libafterstep1 2.1.1-2ubuntu2 [294kB]
Get:7 http://archive.ubuntu.com breezy/universe afterstep 2.1.1-2ubuntu2 [2743kB]
Get:8 http://security.ubuntu.com breezy-security/main libungif4g 4.1.3-2ubuntu0.1 [57.7kB]
Fetched 6592kB in 4m18s (25.5kB/s)
Selecting previously deselected package libltdl3.
(Reading database ... 89411 files and directories currently installed.)
Unpacking libltdl3 (from .../libltdl3_1.5.6-6_amd64.deb) ...
Selecting previously deselected package libmagick6.
Unpacking libmagick6 (from .../libmagick6_6%3a6.2.3.4-1ubuntu1.2_amd64.deb) ...
Selecting previously deselected package menu.
Unpacking menu (from .../archives/menu_2.1.25_amd64.deb) ...
Selecting previously deselected package imagemagick.
Unpacking imagemagick (from .../imagemagick_6%3a6.2.3.4-1ubuntu1.2_amd64.deb) ...
Selecting previously deselected package libungif4g.
Unpacking libungif4g (from .../libungif4g_4.1.3-2ubuntu0.1_amd64.deb) ...
Selecting previously deselected package libafterimage0.
Unpacking libafterimage0 (from .../libafterimage0_2.1.1-2ubuntu2_amd64.deb) ...
Selecting previously deselected package libafterstep1.
Unpacking libafterstep1 (from .../libafterstep1_2.1.1-2ubuntu2_amd64.deb) ...
Selecting previously deselected package afterstep.
Unpacking afterstep (from .../afterstep_2.1.1-2ubuntu2_amd64.deb) ...
Setting up libltdl3 (1.5.6-6) ...

Setting up libmagick6 (6.2.3.4-1ubuntu1.2) ...

Setting up menu (2.1.25) ...

Setting up imagemagick (6.2.3.4-1ubuntu1.2) ...

Setting up libungif4g (4.1.3-2ubuntu0.1) ...

Setting up libafterimage0 (2.1.1-2ubuntu2) ...

Setting up libafterstep1 (2.1.1-2ubuntu2) ...

Setting up afterstep (2.1.1-2ubuntu2) ...

Creating config file /etc/menu-methods/afterstep with new version

Creating config file /etc/X11/afterstep/animate with new version

Creating config file /etc/X11/afterstep/autoexec with new version

Creating config file /etc/X11/afterstep/banner with new version

Creating config file /etc/X11/afterstep/base with new version

Creating config file /etc/X11/afterstep/database with new version

Creating config file /etc/X11/afterstep/pager with new version

Creating config file /etc/X11/afterstep/wharf with new version

Creating config file /etc/X11/afterstep/winlist with new version
mv: cannot stat `x-window-manager': No such file or directory

```

---

### Post by Fass on 2006-08-22
> **Dark Damo said:**
> I ended up getting "afterstep couldnt not be found" or something like that.

Where it says "Exec=afterstep" in the afterstep.desktop file, you will have to put the command you use to start afterstep with the full path to it.

---

