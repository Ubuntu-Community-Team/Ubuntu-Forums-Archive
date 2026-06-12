---
title: "Losing sudo permission"
date: 2009-02-18
forum: General Help
---

### Post by javaman1909 on 2009-02-18
My account is the only account (except root) on Ubuntu. A few days ago, when I read /etc/sudoers, I thought that if I add myself to root group, I can do administrative task without prompt for password. Then, I added myself to root group, nothing happens. Therefore, I delete my account from root group. After that, I lose my sudo permission, although I thought I was in admin group which is granted sudo persmission by default (I didnt delete admin group from /etc/sudoers. 

Now, I end up here. I cant either do any administrative task which required sudo permission nor use root account instead because I havent enabled root account. Can anyone tell me how to restore my sudo permission?

Here is the output of /etc/group
```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:norton
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:norton
fax:x:21:
voice:x:22:
cdrom:x:24:norton
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
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
plugdev:x:46:norton
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
lpadmin:x:108:norton
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
admin:x:123:
norton:x:1000:norton
sambashare:x:124:norton
postfix:x:125:
postdrop:x:126:

```

If you need any information, please tell me, as long as I can get my problem solved.

Thanks in advance.

---

### Post by javaman1909 on 2009-02-18
No need to bother anymore. I have already fixed it by logging to recovery mode, so I can use root account to modify /etc/group.
Thanks.

---

### Post by geirha on 2009-02-18
Boot the ubuntu CD and change the group file from there. Are you unable to get a root shell if you boot in recovery mode too?

---

