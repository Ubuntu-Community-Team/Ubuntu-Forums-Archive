---
title: "Problems with adding a user named &quot;admin&quot;"
date: 2009-04-21
forum: General Help
---

### Post by Jamie Jackson on 2009-04-21
I added a user named "admin" and didn't realize there would be weird consequences. The user "jamie" had admin rights until I did this, and I don't know how to undo what I did. Here's what I'm left with:
```

admin@plubuntu:/media$ groups
admin adm dialout fax cdrom floppy tape audio dip video plugdev fuse

jamie@plubuntu:~$ groups
jamie adm dialout cdrom plugdev lpadmin sambashare

```

This is with Jaunty, FWIW.

Thanks,
Jamie

---

### Post by mgranet on 2009-04-21
I show myself belonging to admin. Maybe you need to add yourself back to the admin group.
```
user@Kubuntu:~$ groups
user adm dialout cdrom plugdev lpadmin admin sambashare vboxusers
```

---

### Post by oOarthurOo on 2009-04-21
It's a known bug. 

[https://bugs.launchpad.net/ubuntu/jaunty/+source/gnome-system-tools/+bug/236305](https://bugs.launchpad.net/ubuntu/jaunty/+source/gnome-system-tools/+bug/236305)

Monitor that bug for ideas on resolving.

---

### Post by Jamie Jackson on 2009-04-27
I'm going to post on the bug report and ask for help resolving. I'm not sure what the smartest solution is, even after reading the comments.

My /etc/groups, in case it helps.
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:jamie,admin
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:jamie,admin
fax:x:21:admin
voice:x:22:
cdrom:x:24:jamie,admin
floppy:x:25:admin
tape:x:26:admin
sudo:x:27:
audio:x:29:pulse,admin
dip:x:30:admin
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:admin
sasl:x:45:
plugdev:x:46:jamie,admin
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
fuse:x:104:admin
ssl-cert:x:105:
lpadmin:x:106:jamie
crontab:x:107:
mlocate:x:108:
ssh:x:109:
avahi-autoipd:x:110:
gdm:x:111:
netdev:x:112:
saned:x:113:
pulse:x:114:
pulse-access:x:115:
pulse-rt:x:116:
messagebus:x:117:
polkituser:x:118:
avahi:x:119:
haldaemon:x:120:
admin:x:1006:
jamie:x:1000:
sambashare:x:122:jamie
heidi:x:1001:
cole:x:1002:
dexter:x:1003:
miles:x:1004:
admubustratir:x:1005:

```

---

### Post by Circle of Owls on 2009-04-27
jharkn's fix worked well for me:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/gnome-system-tools/+bug/236305/comments/3]("https://bugs.launchpad.net/ubuntu/jaunty/+source/gnome-system-tools/+bug/236305/comments/3")

---

### Post by oOarthurOo on 2009-04-28
Nice link. Maybe mark the thread as solved to help other users find the answer more quickly.

---

### Post by Jamie Jackson on 2009-04-28
Thanks all,

For any complete permissions noobs out there, here's the complete fix:

Adding the "admin" user effectively stripped my original user's ("jamie's") admin privileges.

To fix, log into the user who has been stripped of his admin privileges, and open a terminal:
```

# SU to the "admin" user, the only one who has admin rights anymore
su admin
# enter "admin" password, then:
adduser newadminuser
adduser newadminuser admin
deluser admin
adduser jamie admin

```

Actually, now that I think of it, in my case, I think I could have just done:
```

su admin
adduser jamie admin
deluser admin

```

(Which is effectively what mgranet recommended, but I didn't know how to do that at the time.)

Anyway, I just wanted to show how to give a user (who's inadvertently been stripped of admin access) back his admin rights, whereas the original instructions only dealt with getting rid of the non-kosher "admin" user.

---

### Post by Jamie Jackson on 2009-04-28
> **oOarthurOo said:**
> Nice link. Maybe mark the thread as solved to help other users find the answer more quickly.

Oddly enough, that's not an option for me in Thread Tools. Is that feature found elsewhere these days?

---

