---
title: "okay, i'm stumped"
date: 2007-06-26
forum: Debian
---

### Post by kerry_s on 2007-06-26
i changed my debian install to a sudo system with root disabled, but for some reason sudo has stopped asking for a password. i have somethings set to not ask for password for convince, but it's something i've always done, any other commands run with sudo should require a password.
has the setup changed? or is it just a hole? i've waited at least a hour before trying the sudo commands so any prior sudo should have expired, but i haven't typed any password anyways.
any ideas?

my group file

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:user
fax:x:21:
voice:x:22:
cdrom:x:24:user
floppy:x:25:user
tape:x:26:
sudo:x:27:
audio:x:29:user
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
video:x:44:user
sasl:x:45:
plugdev:x:46:user
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
crontab:x:101:
user:x:1000:
messagebus:x:103:
haldaemon:x:104:
powerdev:x:105:
gdm:x:102:
shutdown:x:1001:user
conky:x:1002:user
mousepad:x:1003:user
emelfm:x:1004:user
synaptic:x:1005:user

```

my sudoers

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
user    ALL=(ALL) ALL
%shutdown ALL=(root) NOPASSWD: /sbin/reboot
%conky ALL=(root) NOPASSWD: /usr/bin/conky
%mousepad ALL=(root) NOPASSWD: /usr/bin/mousepad
%emelfm ALL=(root) NOPASSWD: /usr/bin/emelfm
%synaptic ALL=(root) NOPASSWD: /usr/sbin/synaptic

```


never mind folks, after several reboots and a fsck, it's suddenly asking for the password again, must have been some weird all day long fluck. ;)

---

