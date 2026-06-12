---
title: "USB stick mounted as read-only disk"
date: 2006-09-02
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-09-02
Hey, I've read other threads on this, but nothing could help me.

My USB stick is auto-mounted when inserted, but always as a read-only disk. I can't change the permissions, as I'm not the owner (why's that?).
My **etc/fstab** looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda	/media/MEMORYSTICK	vfat	rw,user,noauto,sync	0	0
```
and my **etc/group** looks like this:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:gabriel,barbara
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:gabriel,cupsys,barbara
fax:x:21:gabriel,barbara
voice:x:22:
cdrom:x:24:hal,gabriel,barbara,haldaemon
floppy:x:25:hal,gabriel,barbara,haldaemon
tape:x:26:gabriel,barbara
sudo:x:27:
audio:x:29:gabriel,barbara
dip:x:30:gabriel,barbara
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:gabriel,barbara
sasl:x:45:
plugdev:x:46:hal,gabriel,barbara,haldaemon
staff:x:50:
games:x:60:
users:x:100:gabriel
nogroup:x:65534:
crontab:x:101:
ssh:x:102:
postfix:x:103:
postdrop:x:104:
syslog:x:105:
klog:x:106:
gabriel:x:1000:
lpadmin:x:107:gabriel,barbara
scanner:x:108:gabriel,barbara,cupsys
admin:x:109:gabriel,barbara
messagebus:x:110:
hal:x:111:
slocate:x:112:
saned:x:113:
gdm:x:114:
barbara:x:1001:
dhcp:x:115:
ssl-cert:x:116:
haldaemon:x:117:
```

The user I'm logging in with is gabriel

I really need to use that USB stick, both on windows and on Linux (home & work). How do I make it readable **and **writeable

Thanks


Gabriel

---

