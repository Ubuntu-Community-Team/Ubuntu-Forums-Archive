---
title: "Dr. Web Antivirus on Ubuntu 14.04"
date: 2014-05-08
forum: Gaming &amp; Leisure
---

### Post by ian45 on 2014-05-08
I downloaded the .run file, ran it with 'sh' and it installed perfectly. But then it doesn't start by clicking the icon in dash, nor by terminal. After clickng, the mouse pointer acts like something is loading but nothing happens.
I ran the same installation procedure in opensuse, and it installed, updated and scanned perfectly, and ofcourse it has a icon in the taskbar too.
Any help in successful installation of this program on ubuntu 14.04?

---

### Post by MikeCyber on 2014-05-09
Usually starting via term it gives output on what happens.
so
cd /whereever
./myscanner

You could later also try a gdb back track but that's more complicated.
Try also
ldd myscanner
to see if all needed libs are installed.
I've never used a antivirus on Linux and I use it since 1998...but sometimes I use a outgoing firewall:
[http://sourceforge.net/projects/leopardflower/](http://sourceforge.net/projects/leopardflower/)
like most OSX users do.

---

### Post by ian45 on 2014-05-09
> **MikeCyber said:**
> Usually starting via term it gives output on what happens.
so
cd /whereever
./myscanner

You could later also try a gdb back track but that's more complicated.
Try also
ldd myscanner
to see if all needed libs are installed.
I've never used a antivirus on Linux and I use it since 1998...but sometimes I use a outgoing firewall:
[http://sourceforge.net/projects/leopardflower/](http://sourceforge.net/projects/leopardflower/)
like most OSX users do.

I ran "ldd drweb-workstations_6.0.2.5-1312061656~linux_amd64.run" but it gave this - not a dynamic executable. I already marked it as executable. sudo doesn't help either.

---

### Post by MikeCyber on 2014-05-09
Paste here the terminal output of:
./drweb-workstations_6.0.2.5-1312061656~linux_amd64.run
also of:
ls -la drweb*
and from ldd so we can see it all.
Hmm also try
./drw*
might be a typo or rename it to something alike drweb.run
Well ldd doesn't work on an installer but on installed apps. So 
try again on the installed app whereever this is probably 
~/home or /usr/somwhere
if you don't know you can search either:
whereis drweb*
or
find / -name "*rweb*" 2>/dev/null

---

### Post by ian45 on 2014-05-10
```

root@ubuntu:/home/ubuntu/Downloads# sh ./drweb.run
Creating directory drweb-workstations_6.0.2.5-1312061656~linux_amd64
Verifying archive integrity... All good.
Uncompressing Dr.Web Desktop Security Suite (for Linux workstations)............................................................................................................................................
'/home/ubuntu/Downloads/drweb-workstations_6.0.2.5-1312061656~linux_amd64/setup'
root@ubuntu:/home/ubuntu/Downloads# ls -la drweb*
-rw------- 1 ubuntu ubuntu 161213652 Apr 27 16:07 drweb.run

drweb-workstations_6.0.2.5-1312061656~linux_amd64:
total 156256
drwxrwxrwx 5 root   root        1920 May 10 04:19 .
drwxr-xr-x 3 ubuntu ubuntu        80 May 10 04:19 ..
-r--r--r-- 1 root   root         549 Oct 22  2013 drweb-agent.COPYRIGHTS
-r--r--r-- 1 root   root         108 Oct 22  2013 drweb-agent-es.COPYRIGHTS
-r-xr-xr-x 1 root   root       15330 Oct 22  2013 drweb-agent-es.install
-r-xr-xr-x 1 root   root        6724 Oct 22  2013 drweb-agent-es.remove
-r--r--r-- 1 root   root      117120 Oct 22  2013 drweb-agent-es.sw
-r-xr-xr-x 1 root   root       29845 Oct 22  2013 drweb-agent.install
-r-xr-xr-x 1 root   root       14496 Oct 22  2013 drweb-agent.remove
-r--r--r-- 1 root   root     3331753 Oct 22  2013 drweb-agent.sw
-r--r--r-- 1 root   root         108 Nov 27 12:48 drweb-bases.COPYRIGHTS
-r-xr-xr-x 1 root   root       18089 Nov 27 12:49 drweb-bases.install
-r-xr-xr-x 1 root   root        8272 Nov 27 12:49 drweb-bases.remove
-r--r--r-- 1 root   root   127943364 Nov 27 12:49 drweb-bases.sw
-r--r--r-- 1 root   root         122 Oct  1  2013 drweb-boost147.COPYRIGHTS
-r-xr-xr-x 1 root   root       15560 Oct  1  2013 drweb-boost147.install
-r-xr-xr-x 1 root   root        7953 Oct  1  2013 drweb-boost147.remove
-r--r--r-- 1 root   root     1254460 Oct  1  2013 drweb-boost147.sw
-r--r--r-- 1 root   root         801 Jul  8  2013 drweb-cc.COPYRIGHTS
-r-xr-xr-x 1 root   root      120653 Jul  8  2013 drweb-cc.install
-r-xr-xr-x 1 root   root       56239 Jul  8  2013 drweb-cc.remove
-r--r--r-- 1 root   root    21387929 Jul  8  2013 drweb-cc.sw
-r--r--r-- 1 root   root         108 Nov 21 09:32 drweb-common.COPYRIGHTS
-r-xr-xr-x 1 root   root       30490 Nov 21 09:32 drweb-common.install
-r-xr-xr-x 1 root   root       14223 Nov 21 09:32 drweb-common.remove
-r--r--r-- 1 root   root       69207 Nov 21 09:32 drweb-common.sw
-r--r--r-- 1 root   root         108 Nov 22 15:21 drweb-daemon.COPYRIGHTS
-r-xr-xr-x 1 root   root       25259 Nov 22 15:21 drweb-daemon.install
-r-xr-xr-x 1 root   root       13044 Nov 22 15:21 drweb-daemon.remove
-r--r--r-- 1 root   root      416411 Nov 22 15:21 drweb-daemon.sw
-r--r--r-- 1 root   root        1923 Jul  2  2013 drweb-epm6.0.2-libs.COPYRIGHTS
-r-xr-xr-x 1 root   root       24201 Jul  2  2013 drweb-epm6.0.2-libs.install
-r-xr-xr-x 1 root   root       11345 Jul  2  2013 drweb-epm6.0.2-libs.remove
-r--r--r-- 1 root   root     1083195 Jul  2  2013 drweb-epm6.0.2-libs.sw
-r--r--r-- 1 root   root         855 Jul  2  2013 drweb-epm6.0.2-uninst.COPYRIGHTS
-r-xr-xr-x 1 root   root       16597 Jul  2  2013 drweb-epm6.0.2-uninst.install
-r-xr-xr-x 1 root   root        8551 Jul  2  2013 drweb-epm6.0.2-uninst.remove
-r--r--r-- 1 root   root      295708 Jul  2  2013 drweb-epm6.0.2-uninst.sw
-r--r--r-- 1 root   root         477 Jul  2  2013 drweb-libs32.COPYRIGHTS
-r-xr-xr-x 1 root   root       14724 Jul  2  2013 drweb-libs32.install
-r-xr-xr-x 1 root   root        7832 Jul  2  2013 drweb-libs32.remove
-r--r--r-- 1 root   root      328896 Jul  2  2013 drweb-libs32.sw
-r--r--r-- 1 root   root         477 Jul  2  2013 drweb-libs.COPYRIGHTS
-r-xr-xr-x 1 root   root       13716 Jul  2  2013 drweb-libs.install
-r-xr-xr-x 1 root   root        7039 Jul  2  2013 drweb-libs.remove
-r--r--r-- 1 root   root      326151 Jul  2  2013 drweb-libs.sw
-r--r--r-- 1 root   root         354 Jul  2  2013 drweb-monitor.COPYRIGHTS
-r-xr-xr-x 1 root   root       26075 Jul  2  2013 drweb-monitor.install
-r-xr-xr-x 1 root   root       13089 Jul  2  2013 drweb-monitor.remove
-r--r--r-- 1 root   root      606859 Jul  2  2013 drweb-monitor.sw
-r--r--r-- 1 root   root         108 Jul  2  2013 drweb-scanner.COPYRIGHTS
-r-xr-xr-x 1 root   root       20810 Jul  2  2013 drweb-scanner.install
-r-xr-xr-x 1 root   root       10446 Jul  2  2013 drweb-scanner.remove
-r--r--r-- 1 root   root      262840 Jul  2  2013 drweb-scanner.sw
-r--r--r-- 1 root   root         108 Jul  2  2013 drweb-spider.COPYRIGHTS
-r-xr-xr-x 1 root   root       35002 Jul  2  2013 drweb-spider.install
-r-xr-xr-x 1 root   root       17070 Jul  2  2013 drweb-spider.remove
-r--r--r-- 1 root   root      696807 Jul  2  2013 drweb-spider.sw
-r--r--r-- 1 root   root         108 Jul  2  2013 drweb-updater.COPYRIGHTS
-r-xr-xr-x 1 root   root       19909 Jul  2  2013 drweb-updater.install
-r-xr-xr-x 1 root   root        9994 Jul  2  2013 drweb-updater.remove
-r--r--r-- 1 root   root      179381 Jul  2  2013 drweb-updater.sw
-rw-r--r-- 1 root   root        8942 May 10 04:22 install.log
-rwxr-xr-x 1 root   root        3506 Dec  6 13:02 install.sh
drwxrwxrwx 4 root   root         400 Dec  6 13:02 lib
-rw-r--r-- 1 root   root        7054 Dec  6 13:02 LICENSE
-rw-r--r-- 1 root   root        1338 Dec  6 13:02 license.boost
-rw-r--r-- 1 root   root        1210 Dec  6 13:02 license.expat
-rw-r--r-- 1 root   root       27126 Dec  6 13:02 license.fltk
-rw-r--r-- 1 root   root        1104 Dec  6 13:02 license.fontconfig
-rw-r--r-- 1 root   root       13941 Dec  6 13:02 license.freetype
-rw-r--r-- 1 root   root       18007 Dec  6 13:02 license.gpl2
-rw-r--r-- 1 root   root       36798 Dec  6 13:02 license.gpl-exc
-rw-r--r-- 1 root   root       25284 Dec  6 13:02 license.lgpl2
-rw-r--r-- 1 root   root         662 Dec  6 13:02 license.libcares
-rw-r--r-- 1 root   root        1044 Dec  6 13:02 license.libcurl
-rw-r--r-- 1 root   root        5063 Dec  6 13:02 license.libjpeg
-rw-r--r-- 1 root   root        4205 Dec  6 13:02 license.libpng
-rw-r--r-- 1 root   root        4937 Dec  6 13:02 license.libxml2
-rw-r--r-- 1 root   root        2496 Dec  6 13:02 license.pcre
-rw-r--r-- 1 root   root       14672 Dec  6 13:02 LICENSE.rus
-rw-r--r-- 1 root   root        1136 Dec  6 13:02 license.xau
-rw-r--r-- 1 root   root        1104 Dec  6 13:02 license.xcursor
-rw-r--r-- 1 root   root        1178 Dec  6 13:02 license.xdmcp
-rw-r--r-- 1 root   root        1104 Dec  6 13:02 license.xfixes
-rw-r--r-- 1 root   root       48294 Dec  6 13:02 license.xfree86
-rw-r--r-- 1 root   root        1103 Dec  6 13:02 license.xft
-rw-r--r-- 1 root   root        1104 Dec  6 13:02 license.xrender
-rw-r--r-- 1 root   root        5696 Dec  6 13:02 license.zlib
drwxrwxrwx 4 root   root          80 Dec  6 13:02 locale
-rw-r--r-- 1 root   root         113 Dec  6 13:02 POSTIN-MSG
drwxrwxrwx 2 root   root         300 Dec  6 13:02 scripts
-rwxr-xr-x 1 root   root         705 Dec  6 13:02 setup
-rwxr-xr-x 1 root   root      592133 Dec  6 13:02 setup.real
-rwxr-xr-x 1 root   root        1705 Dec  6 13:02 setup.sh
-rw-r--r-- 1 root   root         365 Dec  6 13:02 setup.types
root@ubuntu:/home/ubuntu/Downloads# ldd drweb*
drweb.run:
    not a dynamic executable
drweb-workstations_6.0.2.5-1312061656~linux_amd64:
ldd: ./drweb-workstations_6.0.2.5-1312061656~linux_amd64: not regular file
root@ubuntu:/home/ubuntu/Downloads# ldd drweb
ldd: ./drweb: No such file or directory
root@ubuntu:/home/ubuntu/Downloads# ldd /usr/bin/drweb
    not a dynamic executable
root@ubuntu:/home/ubuntu/Downloads# ldd /opt/drweb/drweb
    not a dynamic executable
root@ubuntu:/home/ubuntu/Downloads# ldd /opt/drweb/drweb.real
    not a dynamic executable
root@ubuntu:/home/ubuntu/Downloads# ls -la /opt/drweb/drweb
lrwxrwxrwx 1 root root 9 Jul  2  2013 /opt/drweb/drweb -> ldwrap.sh
root@ubuntu:/home/ubuntu/Downloads# ls -la /opt/drweb/drweb.real
-rwxr-xr-x 1 root root 330096 Jul  2  2013 /opt/drweb/drweb.real
root@ubuntu:/home/ubuntu/Downloads# drweb
/usr/bin/drweb: 2: exec: /opt/drweb/drweb.real: not found
root@ubuntu:/home/ubuntu/Downloads# /opt/drweb/drweb.real
-bash: /opt/drweb/drweb.real: No such file or directory
root@ubuntu:/home/ubuntu/Downloads# gksu /opt/drweb/drweb.real
The program 'gksu' is currently not installed. You can install it by typing:
apt-get install gksu
You will have to enable the component called 'universe'
root@ubuntu:/home/ubuntu/Downloads# apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksu
root@ubuntu:/home/ubuntu/Downloads# cd /opt/drweb
root@ubuntu:/opt/drweb# drweb.real
drweb.real: command not found
root@ubuntu:/opt/drweb# 

```

/usr/bin has drweb drweb-cc and drwebdc file containing this code:
```

#!/bin/sh
exec /opt/drweb/`basename $0.real` "$@"

```
application doesn't start by clicking on icon, nor by terminal.
This application used to run fine with previous version: [http://www.youtube.com/watch?v=mSqcABy4GX0](http://www.youtube.com/watch?v=mSqcABy4GX0)
In ubuntu, this app didn't create .drweb hidden folder in home, but in opensuse it did and that's why its working properly in opensuse, I guess.

---

### Post by MikeCyber on 2014-05-10
> **ian45 said:**
> [CODE]
In ubuntu, this app didn't create .drweb hidden folder in home, but in opensuse it did and that's why its working properly in opensuse, I guess.

The hidden stuff in ~ are preferences etc. and are created only on the first app run. So you could easily update while keeping your data with a simple home backup. F.ex. ~./thunderbird contains all 
your emails etc.

Try:
cd /usr/bin
./drweb
and maybe the others? drwebd looks like a daemon/service the runs in the background to me.
/usr/bin has drweb drweb-cc and drwebd

If problems persist paste it again. Maybe also have a look into the 
/home/ubuntu/Downloads/drweb-workstations_6.0.2.5-1312061656~linux_amd64/setup folder if the install was not properly done. I guess it did simply not create 
an icon, as there are many desktops,that's excusable but you might send them 
a bug report.

---

### Post by ian45 on 2014-05-10
> 
I guess it did simply not create 
an icon, as there are many desktops,that's excusable but you might send them
It created icons in dash successfully. Clicking the icon simply gives a "loading" feddback as pointer goes to "loading" mode but app doesn't load.
Here is the output of .drweb:
```

ubuntu@ubuntu:~$ cd /usr/bin
ubuntu@ubuntu:/usr/bin$ ./drweb
./drweb: 2: exec: /opt/drweb/drweb.real: not found
ubuntu@ubuntu:/usr/bin$ 

```
I also tried installing the app in root login mode but no help. I am not going to report this, will simply install another antivirus app and use peerguardian, wireshark, etc.
All the above reporting is done through live-cd ubuntu, but I correctly rememeber that issue was same with installed version.
I am continuing to use openSUSE until I find any major reason switch to another distro.

---

### Post by MikeCyber on 2014-05-10
Maybe because it's a live cd? I've left Suse many years ago when Ubuntu introduced online repos and also because of annoying sound problems on Suse.

---

