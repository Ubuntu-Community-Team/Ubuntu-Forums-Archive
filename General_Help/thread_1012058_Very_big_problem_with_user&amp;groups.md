---
title: "Very big problem with user&amp;groups"
date: 2008-12-15
forum: General Help
---

### Post by psychok9 on 2008-12-15
I added pulse-rt with a guide on google (for fix pulse stuttering and erros on pulseaudio start from console), but the result is the wiping of my permissions/user&groups and sudoers file.
Started on recovery mode I fixed with root shell, and visudo.
Now how can I fix my user&group wiped to default?
I see from folder proprierties groups existing are only  "myusername" and "pulse-rt" -_-"
I can't access "users-admin", with "gksudo users-admin" all it's grey!

I hope that you can help me, it's very appreciated!

Thank you!

---

### Post by taurus on 2008-12-15
Just add your username to groups adm, cdrom, audio, games,video, plugdev, lpadmin, and admin in /etc/group.

---

### Post by psychok9 on 2008-12-16
For the next time...
1) What's the command?
(I've fixed with format :().

2) How can I backup my actual user&group configuration?

Thank you!

---

### Post by doobiest on 2008-12-16
well you've got /etc/group /etc/passwd and  /etc/shadow  one's groups the other is user/password association.

---

### Post by psychok9 on 2008-12-19
I don't understand your answer.
**Ubuntu has destroyed again sudo/user&groups!!!**
This happened when I remove ffmpeg, x264, gstreamer-bad and totem!
How can I restore my previous configuration?
It's realy amazing that happens something like this when you do something simple as what I did.

Thank you in advance!

---

### Post by psychok9 on 2008-12-19
I've fixed with recovery prompt shell, and the command:
```
adduser gianluca admin
adduser gianluca adm
```
And sudo works now.
I would like to know where I have to put my username so that I can restore standard & default Ubuntu configuration.

---

### Post by taurus on 2008-12-19
In /etc/group.

---

### Post by psychok9 on 2008-12-19
What /etc/group?
This is my gedit /etc/group:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:myusername
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:myusername
fax:x:21:myusername
voice:x:22:
cdrom:x:24:myusername
floppy:x:25:
tape:x:26:myusername
sudo:x:27:
audio:x:29:pulse,myusername
dip:x:30:myusername
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:myusername
sasl:x:45:
plugdev:x:46:myusername
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:myusername
nvram:x:105:
fuse:x:106:myusername
ssl-cert:x:107:
lpadmin:x:108:myusername
crontab:x:109:
mlocate:x:110:
ssh:x:111:
avahi-autoipd:x:112:
gdm:x:113:
netdev:x:114:myusername
pulse:x:115:
pulse-access:x:116:
pulse-rt:x:117:myusername
saned:x:118:
messagebus:x:119:
polkituser:x:120:
avahi:x:121:
haldaemon:x:122:
admin:x:123:myusername
myusername:x:1000:
sambashare:x:124:myusername
winbindd_priv:x:125:
Debian-exim:x:126:
vboxusers:x:127:myusername
```
Is it ok/default?
Thank you!

---

### Post by taurus on 2008-12-19
That looks fine to me unless you want to add yourself to group games if you are playing games.

---

