---
title: "Gui tool destroyed /etc/group"
date: 2009-02-23
forum: General Help
---

### Post by boban on 2009-02-23
Hi!

I run into serious problems. I wanted to add myself to audio group via a default GUI tool (System->Administration->Users and Groups). I clicked "Unlock", gave my password and entered "User Privileges" tab and... noticed nothing was there. 

I thought that only GUI tool was messed up, so I dropped down to terminal. And there was another surprise - I couldn't use sudo (permission denied). Fortunately I still had a "Users and Groups" program opened and I managed to create password for root. Using visudo as a rootI got my sudo permissions back. 

But what is worst - my /etc/group is totally messed up. Here is how this file looks like now:

```

sudo cat /etc/group
root:x:0:
nogroup:x:65534:
boban:x:1000:boban

```

I presume that after rebooting my system will be unusable. Unfortunately I do not have backup of /etc. Also I just cannot reinstall ubuntu right now (I have much work to do)... Is there a way to fix this file?

---

### Post by taurus on 2009-02-23
What's the output of this command from a terminal?

```
ls -la /etc/group*
```

---

### Post by prinny42 on 2009-02-23
If there doesn't happen to be a backup of it, I don't know if this'll work, but this is mine:

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:(My Username)
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:(My Username)
fax:x:21:
voice:x:22:
cdrom:x:24:(My Username)
floppy:x:25:(My Username)
tape:x:26:
sudo:x:27:
audio:x:29:pulse,(My Username)
dip:x:30:(My Username)
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:(My Username)
sasl:x:45:
plugdev:x:46:(My Username)
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
dhcp:x:102:
syslog:x:103:
klog:x:104:
scanner:x:105:hplip
nvram:x:106:
fuse:x:107:(My Username)
ssl-cert:x:108:
lpadmin:x:109:(My Username)
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:115:(My Username)
pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:
messagebus:x:119:
avahi:x:120:
netdev:x:121:
polkituser:x:122:
haldaemon:x:123:
(My Username):x:1000:
winbindd_priv:x:124:
```

Of course, you would have to replace all the "(My Username)"s with your username.  You can do that by going into vim and hitting the colon.  Then type
```
%s/\(My\ Username\)/(The thing that is actually your username)/g
```
ETA: Hit enter after typing that of course.

Then hit colon again, type "wq" (minus quotes), and hit enter to save and quit.

---

### Post by boban on 2009-02-23
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la /etc/group*
```

Thanks for quick reply. 

```

-rw-r--r-- 1 root root 46 2009-02-23 17:11 /etc/group
-rw------- 1 root root 46 2009-02-23 17:11 /etc/group-

```

But unfortunately the backup file is also messed up :(. I think I managed to enter my user two times from the GUI app.

---

### Post by boban on 2009-02-23
> **prinny42 said:**
> If there doesn't happen to be a backup of it, I don't know if this'll work, but this is mine:


I think I will have to try this way. Hopefully ubuntu has standard group numbers across installations...

---

### Post by boban on 2009-02-23
> **boban said:**
> I think I will have to try this way. Hopefully ubuntu has standard group numbers across installations...

It seems to be working... but only partially. F.e. /var/lib/mysql belongs to avahi! I think I will have to reinstall Ubuntu :/. 

I think I know why "Users and Groups" managed to destroy my /etc/group. I think I had a syntax error in it (edited it manually some time ago). But I do not think that syntax error in one line should result in destroyed file.

---

