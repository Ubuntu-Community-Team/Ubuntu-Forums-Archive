---
title: "Users Settings dialogue box doesn't show my username"
date: 2009-01-23
forum: General Help
---

### Post by tptbz on 2009-01-23
Hello,

I'm using Ubuntu 8.10.  My username is "brian".  That's the account I created during installation.

I wanted to add my user to a new group.  So I opened the "Users Settings" dialogue box by clicking, System->Administration->Users and Groups.  But, the only user shown is "root".  I would have thought that I would see my username, "brian" as well.

Did I do something wrong?

I attached two pics to show the "Users Settings" and that my username is "brian".

Thank you.

---

### Post by spiderbatdad on 2009-01-23
My first thought is that you booted with the live cd still in, or booted into recovery mode.

---

### Post by mssever on 2009-01-24
That's an odd problem. Neither of spiderbatdad's ideas fit the screenshots. Obviously the user "brian" exists on the system--witness the second screenshot.

Another user recently had an issue where the UIDs of their users were below 1000 (because they'd been created on a distro that starts normal users with lower UIDs than Ubuntu does). Perhaps you could post the result of issuing the "id" command with no arguments. That would confirm or rule out my hypothesis.

Of course, if you just need to add your user to a group and don't care about fixing this particular problem, just edit /etc/group to your heart's content. Usernames are in the last field of each line, separated by commas (no spaces). See ```
man 5 group
```for more. Note that changes won't take effect until you log out and back in--this applies no matter how you edit your groups.

---

### Post by tptbz on 2009-01-24
Hi,

Here is the output:
brian@xps:~/dl1$ id
uid=500(brian) gid=500(brian) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),500(brian)

You wrote, "because they'd been created on a distro that starts normal users with lower UIDs than Ubuntu does".  I switched from openSUSE to Ubuntu a couple of days ago.
I keep my "home" directory on a different hard drive than my "root" folder.  So, when I switched distros I kept my "home" folder intact and selected not to format it during the Ubuntu installation.

In the past when I would change distros I would have to run the following command as root on my "home" directory so that I could get back my read and write access.  But, after installing Ubuntu I was able to read and write to my "home" and didn't run:
#chown --recursive brian: /home/brian

Do you think I should run the chown command above?

---

### Post by taurus on 2009-01-24
The first user that you created during the installing process has an UID of 1000.  That user belongs to group admin so he/she can have root privilege.  Since you use the same UID, 500, from OpenSUSE, you need to make sure you add yourself to group admin in /etc/group.

```
cat /etc/group
```

---

### Post by tptbz on 2009-01-24
```
brian@xps:~/dl1$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:brian
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:brian
fax:x:21:
voice:x:22:
cdrom:x:24:brian
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
plugdev:x:46:brian
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
lpadmin:x:108:brian
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
admin:x:123:brian
brian:x:500:
sambashare:x:124:brian

```

---

### Post by mssever on 2009-01-24
> **tptbz said:**
> Hi,

Here is the output:
brian@xps:~/dl1$ id
uid=500(brian) gid=500(brian) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),500(brian)

You wrote, "because they'd been created on a distro that starts normal users with lower UIDs than Ubuntu does".  I switched from openSUSE to Ubuntu a couple of days ago.
I keep my "home" directory on a different hard drive than my "root" folder.  So, when I switched distros I kept my "home" folder intact and selected not to format it during the Ubuntu installation.

In the past when I would change distros I would have to run the following command as root on my "home" directory so that I could get back my read and write access.  But, after installing Ubuntu I was able to read and write to my "home" and didn't run:
#chown --recursive brian: /home/brian

Do you think I should run the chown command above?
OK, that's what I expected. I just saw another person with this problem a few days ago. Basically, you have two options:

[LIST=1]
[*]Adjust your UID. This is a multi-step process:
[LIST=1]
[*]Edit /etc/passwd and change your UID. It's the third field. Set it to 1000 or higher and make sure it's unique.
[*]chown all your files back to your user (they'll show that they're owned by 500, not brian). You might have to log out and back in before taking this step. If so, X will probably refuse to start, so you'll have to work from a console until you get the ownership fixed.
[*]Make sure you don't chown something you shouldn't, or you'll have more problems and could end up having to reinstall.
[/LIST]
[*]Fire up gconf-editor and enable the key /apps/gnome-system-tools/users/showall. If you choose this route, all users on your system will show up in Users and Groups, even system accounts that you shouldn't mess with.
[/LIST]

---

### Post by 55tptag on 2009-01-27
> **mssever said:**
> 
Adjust your UID. This is a multi-step process:
[LIST=1]
[*]Edit /etc/passwd and change your UID. It's the third field. Set it to 1000 or higher and make sure it's unique.
[*]chown all your files back to your user (they'll show that they're owned by 500, not brian). You might have to log out and back in before taking this step. If so, X will probably refuse to start, so you'll have to work from a console until you get the ownership fixed.
[*]Make sure you don't chown something you shouldn't, or you'll have more problems and could end up having to reinstall.
[/LIST]


Hi mssever,

I did the steps you suggested and it fixed the problem. I also attached the "User Settings" dialog box to show that my username now is listed.

Thanks for your time and help.

---

