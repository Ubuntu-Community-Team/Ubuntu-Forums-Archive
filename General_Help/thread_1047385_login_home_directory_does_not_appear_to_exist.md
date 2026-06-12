---
title: "login: home directory does not appear to exist"
date: 2009-01-22
forum: General Help
---

### Post by lookas on 2009-01-22
# I can’t login on my Xubuntu 2.6.15-51-386
# if I do login of user "XY" in Xfce session go this error:

Your home directory is listed as: '/home/XY' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory?
It is unlikely anything will work unless you use a failsafe session.

# if I choice No -> go back to login screen
# if I choice Yes -> go to this error:

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users.

# after ->

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.
Details (~/.xsession-errors file)
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg –a –w /var/log/wtmp –u /var/log/utmp – x "/var/lib/gdm/:0.Xservers" –h " " –l " :0" "XY"
/etc/gdm/Xsession: Beginning session setup…
/usr/bin/startxfce4: X server already running on display :0
xfce4-session: Unable to access file /home/XY/ .ICEautority: Permission denied

# Please, can somebody help me?
# Thanx

---

### Post by taurus on 2009-01-22
Boot into recovery mode from GRUB menu and see if there is even a home directory for XY!

```
ls -la /home
```
If there is, then either permissions or ownership are wrong.

```
chown -R XY:XY /home/XY
chmod -R 755 /home/XY
chmod 644 /home/XY/.dmrc
shutdown -r now
```
Now, see if you can log back in as XY.

---

### Post by lookas on 2009-01-22
thanx ;), but that is not it
the same problem always remaining :(

---

### Post by taurus on 2009-01-22
What is not it?  Is there even a $HOME for XY?

```
ls -la /home
```

---

### Post by lookas on 2009-01-22
so, that command write:
4 drwxr-xr-x 13 XY XY 4096 ...

and those commands of your second code are not change nothing

---

### Post by lookas on 2009-01-22
if I creat a new user, make the identical problem with home directory

---

### Post by taurus on 2009-01-22
> **lookas said:**
> so, that command write:
4 drwxr-xr-x 13 XY XY 4096 ...

and those commands of your second code are not change nothing

There is no XY directory under /home so that is why it's complaining.

> **lookas said:**
> if I creat a new user, make the identical problem with home directory

So your system wouldn't even let you create a new user?  Do you have a separate /home or you only have one large root partition, /?  What are the outputs of these commands from a prompt?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by lookas on 2009-01-24
then here's what came out
> root@XY:~# fdisk -l
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4681    37600101   83  Linux
/dev/hda2            4682        4065     1477980    5  Extended
/dev/hda5            4682        4065     1477948+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38728   311082628+  83  Linux
/dev/sda2           38729       38913     1486012+   5  Extended
/dev/sda5           38729       38913     1485981   82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38728   311082628+  83  Linux
/dev/sdb2           38729       38913     1486012+   5  Extended
/dev/sdb5           38729       38913     1485981   82  Linux swap / Solaris


> root@XY:~# cat /etc/fstab
# /etc/fstab: statistic file system information.
#
# <file system> <mount point>      <type>  <options>       <dump>  <pass>
proc            /proc              proc    defaults        0       0
/dev/hda1       /                  ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none               swap    sw              0       0
/dev/hdb        /media/cdrom0      udf,iso9660 user,noauto     0       0
/dev/sda1       /home/volume2      ext3    defaults,errors=remount-ro 0       1
/dev/sdb1       /home/volume3      ext3    defaults,errors=remount-ro 0       1


> root@XY:~# df &#8211;h
Filesystem        Size  Used Avail Use% Mounted on
/dev/hda1          36G  2.1G   32G   7% /
varrun            249M   12K  249M   1% /var/run
varlock           249M  4.0K  249M   1% /var/lock
udev              249M  148K  248M   1% /dev
devshm            249M     0  249M   0% /dev/shm
lrm               249M   19M  230M   8% /lib/modules/2.6.15-51-386/volatile
/dev/sda1         293G  277G  291M 100% /home/volume2
/dev/sdb1         293G  169G  109G  61% /home/volume3


---

### Post by lookas on 2009-02-11
Please, can anybody help me?:confused:

---

