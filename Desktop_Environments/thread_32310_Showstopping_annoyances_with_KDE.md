---
title: "Showstopping annoyances with KDE"
date: 2005-05-07
forum: Desktop Environments
---

### Post by NerftheSmurf on 2005-05-07
So I tried Kubuntu a while ago and was just getting warmed up to it until something very strange happened. Every time I opened any KDE application I'd get a pop up message that says 'MIME type not found: application/octet-stream'

This even happens when I try to run KDE applications in GNOME like amarok or k3b. Also recently, and I don't know if this is related or not, but I've had trouble upgrading the kdelibs-data package. The transcript goes like so:

```
$ sudo apt-get update; sudo apt-get upgrade
Get:1 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security Release
Hit http://us.archive.ubuntu.com hoary Release
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Get:5 http://us.archive.ubuntu.com hoary-updates Release [16.8kB]
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit ftp://ftp.nerim.net stable Release.gpg
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit ftp://ftp.nerim.net unstable Release.gpg
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit ftp://ftp.nerim.net testing Release.gpg
Hit http://us.archive.ubuntu.com hoary/main Sources
Get:6 ftp://ftp.nerim.net stable Release [1348B]
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Get:7 ftp://ftp.nerim.net unstable Release [2528B]
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit ftp://ftp.nerim.net testing Release
Hit ftp://ftp.nerim.net stable/main Packages
Hit ftp://ftp.nerim.net unstable/main Packages
Hit ftp://ftp.nerim.net testing/main Packages
Fetched 20.9kB in 6s (3423B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  realplayer
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
10 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
(Reading database ... 130038 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

I tried moving that /usr/share/icons/default.kde file (which is a symbolic link apparently) but I still get that same message even though that file does not exist! My sources.list is straight out of the ubuntu guide page so I have no idea what's wrong.

Does anyone know what the heck is going on???

---

### Post by johnprgr on 2005-05-07
This has been answered in other places.  I don't remember exactly where I found the answer, but I know it I didn't figure it out myself.

Basically just do 'sudo dpkg -i --force-overwrite /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb'

Hope this helps

---

### Post by NerftheSmurf on 2005-05-08
Thanks, that worked for that problem.

Additionally I was able to fix that other problem with something I found on the internet.

Posting for the benefit of others who may check this board in the future:

> It happend to me too when I upgraded my system (I use Slackware). The solution was to create a new MIME type named "octet-stream" using KDE's control center.

In the control center select "KDE Componentes" then "File Associations". In the window that appears click on the Add... button. A small dialog box will appear. Select "application" fom the drop down box, and type "octet-stream" (without the quotes) in the blank labeled Type name. Click OK to add the new MIME type. After you click OK another window appears. I had to type something in the "Filename Patterns" box so that my new MIME type would be actually saved. Because if I left it all blank, it would not be saved. So I just typed "octet-stream" (again, without the quotes). Make sure you don't use an already existent filename pattern or any wildcards. Make sure to click Apply before clicking OK. That's it. I hope it helps.


[http://lists.debian.org/debian-kde/2005/03/msg00165.html](http://lists.debian.org/debian-kde/2005/03/msg00165.html)

---

