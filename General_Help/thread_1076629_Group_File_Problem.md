---
title: "Group File Problem"
date: 2009-02-21
forum: General Help
---

### Post by ChrisB111 on 2009-02-21
I used the Users and Groups app in gnome to create an audio group and add myself to it. When I started up the computer later it complained during boot up about the groups so I booted off a live cd and had a look at the group file, it only had 2 groups. I copied the group file from the live cd to replace it this now allows it to boot but things are still not working properly. I cant access the internet and I don't think I have sudo permissions. I have added two users on this machine chris (my user) and help (the user I use to login as if I break chris). They should have the same permissions, the normal admin stuff but I haven't added help to all the right groups. All I want to do at the moment is get chris working properly. This is my group file.

Thanks,

Chris

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:chris,help
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:chris,help
fax:x:21:
voice:x:22:
cdrom:x:24:chris,help
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse,chris,help,root
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:chris,help
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:
lpadmin:x:108:chris,help
crontab:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
gdm:x:113:
netdev:x:114:
pulse:x:115:
pulse-access:x:116:
pulse-rt:x:117:
saned:x:118:
messagebus:x:119:
polkituser:x:120:
avahi:x:121:
haldaemon:x:122:
admin:x:123:chris,help
ubuntu:x:999:
sambashare:x:124:chris,help
```

---

### Post by dcstar on 2009-02-21
> **ChrisB111 said:**
> I used the Users and Groups app in gnome to create an audio group and add myself to it. When I started up the computer later it complained during boot up about the groups so I booted off a live cd and had a look at the group file, it only had 2 groups. I copied the group file from the live cd to replace it this now allows it to boot but things are still not working properly. I cant access the internet and I don't think I have sudo permissions. I have added two users on this machine chris (my user) and help (the user I use to login as if I break chris). They should have the same permissions, the normal admin stuff but I haven't added help to all the right groups. All I want to do at the moment is get chris working properly. This is my group file.

Thanks,

Chris

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:chris,help
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:chris,help
fax:x:21:
voice:x:22:
cdrom:x:24:chris,help
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse,chris,help,root
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:chris,help
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:
lpadmin:x:108:chris,help
crontab:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
gdm:x:113:
netdev:x:114:
pulse:x:115:
pulse-access:x:116:
pulse-rt:x:117:
saned:x:118:
messagebus:x:119:
polkituser:x:120:
avahi:x:121:
haldaemon:x:122:
admin:x:123:chris,help
ubuntu:x:999:
sambashare:x:124:chris,help
```

Is your gshadow file also fixed?

---

### Post by ChrisB111 on 2009-02-22
Probably not, is the group file shadowed like the passwd file? I will have a look and see if I can fix it.

Thanks,

Chris

---

### Post by ChrisB111 on 2009-02-22
My Group file now looks like the copy below> I was having a look at the passwd file to see if any users were refering to non-existent groups when I realised that all the users where in the group no-group. I'm not sure if this is correct. There is a copy of my passwd file below.

Thanks,

Chris

PASSWD
```
root:x:0:65534:root:/root:/bin/bash
daemon:x:1:65534:daemon:/usr/sbin:/bin/sh
bin:x:2:65534:bin:/bin:/bin/sh
sys:x:3:65534:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:65534:games:/usr/games:/bin/sh
man:x:6:65534:man:/var/cache/man:/bin/sh
lp:x:7:65534:lp:/var/spool/lpd:/bin/sh
mail:x:8:65534:mail:/var/mail:/bin/sh
news:x:9:65534:news:/var/spool/news:/bin/sh
uucp:x:10:65534:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:65534:proxy:/bin:/bin/sh
www-data:x:33:65534:www-data:/var/www:/bin/sh
backup:x:34:65534:backup:/var/backups:/bin/sh
list:x:38:65534:Mailing List Manager:/var/list:/bin/sh
irc:x:39:65534:ircd:/var/run/ircd:/bin/sh
gnats:x:41:65534:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:65534::/var/lib/libuuid:/bin/sh
syslog:x:101:65534::/home/syslog:/bin/false
klog:x:102:65534::/home/klog:/bin/false
hplip:x:103:65534:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:65534:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:105:65534:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:106:65534:PulseAudio daemon,,,:/var/run/pulse:/bin/false
saned:x:107:65534::/home/saned:/bin/false
messagebus:x:108:65534::/var/run/dbus:/bin/false
polkituser:x:109:65534:PolicyKit,,,:/var/run/PolicyKit:/bin/false
avahi:x:110:65534:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:111:65534:Hardware abstraction layer,,,:/var/run/hald:/bin/false
chris:x:1000:65534:Chris,,,:/home/chris:/bin/bash
beagleindex:x:112:65534::/var/cache/beagle:/bin/false
help:x:1001:65534:,,,:/home/help:/bin/bash
tomcat6:x:113:65534::/usr/share/tomcat6:/bin/false
lire:x:114:65534:Lire,,,:/var/lib/lire:/bin/sh
Debian-exim:x:115:65534::/var/spool/exim4:/bin/false
test:x:116:65534::/home/test:/bin/false
```

GROUP
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:chris,help
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:chris,help
kmem:x:15:
dialout:x:20:chris,help
fax:x:21:
voice:x:22:
cdrom:x:24:chris,help
floppy:x:25:chris,help
tape:x:26:
sudo:x:27:
audio:x:29:pulse,chris,help
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:chris,help
staff:x:50:
games:x:60:
users:x:100:chris,help
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:chris,help
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:
lpadmin:x:108:chris,help
crontab:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
gdm:x:113:
netdev:x:114:
pulse:x:115:
pulse-access:x:116:
pulse-rt:x:117:
saned:x:118:
messagebus:x:119:
polkituser:x:120:
avahi:x:121:
haldaemon:x:122:
admin:x:123:chris,help
ubuntu:x:999:
sambashare:x:124:chris,help
```

---

### Post by larkaen on 2009-12-08
I had the same problem - when using the User and Group GUI, it nuked the /etc/group file only leaving two entries.  

I had a backup of the file to fix it with, but is there any word on WHY it happens?

---

### Post by ChrisB111 on 2009-12-10
I think what caused it in my case is I tried to use gnome to edit the audio group, I created a audio group and added myself to it, I think as there was an audio group in the file something happened and the file became empty.

Chris

---

