---
title: "installation problem"
date: 2009-03-01
forum: General Help
---

### Post by TwistedGhost on 2009-03-01
ok so i already have ubuntu installed with like 50 gb of music
it was having problems with the graphics not wanting to be changed 
so i reinstalled into a new partition but i kept the old 1
what is the easiest way to eather get all my stuff from the old partition onto the new one or fix the old partition and delete the new one 
please let me know which is easier and how to do it thanxs

---

### Post by TwistedGhost on 2009-03-02
BUMP 
i really need some help with this please

---

### Post by Ben Crisford on 2009-03-02
So you have basically partitioned the disk four ways?

I'm a little confused :confused:.

p.s. I'll give you a BUMP ;).

---

### Post by taurus on 2009-03-02
If you want to access the "old" partition to get your files, you first need to mount it.  Do you know which partition you installed it first that X server doesn't work anymore?

Open a terminal and post the outputs of these commands, running one command at a time.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by TwistedGhost on 2009-03-02
> **taurus said:**
> If you want to access the "old" partition to get your files, you first need to mount it.  Do you know which partition you installed it first that X server doesn't work anymore?

Open a terminal and post the outputs of these commands, running one command at a time.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```
sudo fdisk -l
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8de8f9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18858   151476853+  83  Linux
/dev/sda2           18859       24321    43881547+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris
/dev/sda6           18859       23730    39134277   83  Linux
/dev/sda7           23731       23944     1718923+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 252 MB, 252968960 bytes
8 heads, 61 sectors/track, 1012 cylinders
Units = cylinders of 488 * 512 = 249856 bytes
Disk identifier: 0x058d058c

   Device Boot      Start         End      Blocks   Id  System


sudo blkid
/dev/sda1: UUID="4297935c-6563-4257-9d19-391692daa7df" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="21570d42-f2b3-4d33-a667-242ff77fc1bf" 
/dev/sda6: UUID="e8bfb8b0-7cf3-4cf3-8e2e-416933266f71" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="cf38211c-6e6f-46ea-9e91-e3d0ebdaf3ca" 

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e8bfb8b0-7cf3-4cf3-8e2e-416933266f71 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=cf38211c-6e6f-46ea-9e91-e3d0ebdaf3ca none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              37G  3.7G   32G  11% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M   96K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.9M  502M   1% /dev
tmpfs                 505M  588K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1             143G  142G     0 100% /media/disk



what it was was i broke the graphics and could not fix them so i reinstalled keeping the old partition and making a new one
what i am trying to do is eather fix the old partition or get all my files onto the new partition which ever is easyer then delete the partition i dont need which ever it may be

---

### Post by crokett on 2009-03-02
what partition is the old install on?  In any case, to access the files you need to mount the partition and you need a mount point.  So open a terminal session and type:

mkdir oldstuff

then to mount the partition assuming it is installed in partition 1 and your home directory is called twistedghost

mount /dev/sda1 /home/twistedghost/oldstuff

Then you can browse the oldstuff folder and should see all the files from the old install.

---

### Post by TwistedGhost on 2009-03-02
ok so what is the easiest way to transfer all of my files from the old partition to the new partition?

and then delete the old partition


please help i am getting closer but still have two versions of ubuntu installed on my computer

---

### Post by taurus on 2009-03-02
Your old root partition, /, is /dev/sda1 and it is currently mounted to /media/disk which is somehow maxed out, all 142GB of it!  And your old swap partition is /dev/sda5.

So, your old personal files is probably in /media/disk/home/*your_old_username*.

```
ls -la /media/disk/home/*your_old_username*
```
Replace *your_old_username* with the name that you logged in with on your old install.

---

### Post by TwistedGhost on 2009-03-02
> **taurus said:**
> Your old root partition, /, is /dev/sda1 and it is currently mounted to /media/disk which is somehow maxed out, all 142GB of it!  And your old swap partition is /dev/sda5.

So, your old personal files is probably in /media/disk/home/*your_old_username*.

```
ls -la /media/disk/home/*your_old_username*
```
Replace *your_old_username* with the name that you logged in with on your old install.

can you please explain how that will transfer all of my files from my old partition to my new partition

---

### Post by taurus on 2009-03-02
Where did you store your files in your old $HOME?  What was the login name that you use with the old install?

```
ls -la /media/disk/home
```
What is your login name for the new install and where do you want to move/save those files to?

```
ls -la ~
```

If you want to move files from your old $HOME to your current $HOME, use nautilus and navigate to your old $HOME--/media/disk/home/your_old_username.

```
nautilus
```

---

### Post by TwistedGhost on 2009-03-03
> **taurus said:**
> Where did you store your files in your old $HOME?  What was the login name that you use with the old install?

```
ls -la /media/disk/home
```
What is your login name for the new install and where do you want to move/save those files to?

```
ls -la ~
```

If you want to move files from your old $HOME to your current $HOME, use nautilus and navigate to your old $HOME--/media/disk/home/your_old_username.

```
nautilus
```

so the old user is twistedghost the new user is twistedghost and any time i try to move anything from the ole partition to the new one it just uses more space rather than the same space

---

### Post by TwistedGhost on 2009-03-03
i tried to enter the codes that you told me and it said that the media could not be found

---

### Post by TwistedGhost on 2009-03-03
> **taurus said:**
> Where did you store your files in your old $HOME?  What was the login name that you use with the old install?

```
ls -la /media/disk/home
```
What is your login name for the new install and where do you want to move/save those files to?

```
ls -la ~
```

If you want to move files from your old $HOME to your current $HOME, use nautilus and navigate to your old $HOME--/media/disk/home/your_old_username.

```
nautilus
```

twistedghost@twistedghost-desktop:~$ ls -la /media/disk/home
total 12
drwxr-xr-x  3 root         root         4096 2009-02-13 23:39 .
drwxr-xr-x 20 root         root         4096 2009-03-01 16:55 ..
drwxr-xr-x 47 twistedghost twistedghost 4096 2009-03-01 15:56 twistedghost
twistedghost@twistedghost-desktop:~$ 
twistedghost@twistedghost-desktop:~$ ls -la ~
total 13476
drwxr-xr-x 43 twistedghost twistedghost     4096 2009-03-03 14:30 .
drwxr-xr-x  3 root         root             4096 2009-03-01 17:08 ..
drwx------  3 twistedghost twistedghost     4096 2009-03-01 20:06 .adobe
drwxr-xr-x  3 twistedghost twistedghost     4096 2009-03-03 10:56 .avidemux
drwxr-xr-x 13 twistedghost twistedghost     4096 2009-03-03 14:30 .azureus
-rw-------  1 twistedghost twistedghost     1257 2009-03-03 12:42 .bash_history
-rw-r--r--  1 twistedghost twistedghost      220 2009-03-01 17:08 .bash_logout
-rw-r--r--  1 twistedghost twistedghost     3115 2009-03-01 17:08 .bashrc
drwx------  2 twistedghost twistedghost     4096 2009-03-02 13:09 .bogofilter
drwxr-xr-x  6 twistedghost twistedghost     4096 2009-03-03 10:57 .cache
drwx------  3 twistedghost twistedghost     4096 2009-03-01 20:03 .compiz
drwxr-xr-x 12 twistedghost twistedghost     4096 2009-03-03 11:55 .config
drwx------  3 twistedghost twistedghost     4096 2009-03-01 17:49 .dbus
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-03 12:32 Desktop
-rw-r--r--  1 twistedghost twistedghost       51 2009-03-03 00:39 .devede
-rw-------  1 twistedghost twistedghost       28 2009-03-03 14:07 .dmrc
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-02 20:30 Documents
-rw-------  1 twistedghost twistedghost       16 2009-03-01 17:49 .esd_auth
drwxr-xr-x  8 twistedghost twistedghost     4096 2009-03-02 17:34 .evolution
lrwxrwxrwx  1 twistedghost twistedghost       26 2009-03-01 17:08 Examples -> /usr/share/example-content
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-02 18:14 .fontconfig
drwxr-xr-x  5 twistedghost twistedghost     4096 2009-03-03 14:08 .gconf
drwx------  2 twistedghost twistedghost     4096 2009-03-03 14:31 .gconfd
-rw-r-----  1 twistedghost twistedghost        0 2009-03-03 14:09 .gksu.lock
drwx------ 10 twistedghost twistedghost     4096 2009-03-03 12:41 .gnome2
drwx------  2 twistedghost twistedghost     4096 2009-03-01 17:49 .gnome2_private
drwx------  2 twistedghost twistedghost     4096 2009-03-01 17:49 .gnupg
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-02 18:36 .gstreamer-0.10
-rw-r--r--  1 twistedghost twistedghost      136 2009-03-03 14:19 .gtk-bookmarks
dr-x------  2 twistedghost twistedghost        0 2009-03-03 14:07 .gvfs
-rw-------  1 twistedghost twistedghost      935 2009-03-03 14:07 .ICEauthority
drwx------  2 twistedghost twistedghost     4096 2009-03-03 00:44 .kino-history
-rw-r--r--  1 twistedghost twistedghost     2969 2009-03-03 00:52 .kinorc
drwx------  3 twistedghost twistedghost     4096 2009-03-01 17:49 .local
drwx------  3 twistedghost twistedghost     4096 2009-03-01 20:06 .macromedia
drwxr-xr-x  5 twistedghost twistedghost     4096 2009-03-03 00:52 .miro
drwxr-xr-x  5 twistedghost twistedghost     4096 2009-03-02 18:16 .mozilla
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-03 00:25 .mplayer
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-01 17:49 Music
drwxr-xr-x  3 twistedghost twistedghost     4096 2009-03-02 13:51 .nautilus
drwxr-xr-x 20 root         root             4096 2009-03-01 16:55 oldstuff
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-02 16:28 Pictures
-rw-r--r--  1 twistedghost twistedghost      675 2009-03-01 17:08 .profile
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-01 17:49 Public
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-01 17:49 .pulse
-rw-------  1 twistedghost twistedghost      256 2009-03-01 17:49 .pulse-cookie
-rw-------  1 twistedghost twistedghost     7693 2009-03-03 14:18 .recently-used.xbel
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-03 00:25 .spumux
-rw-r--r--  1 twistedghost twistedghost        0 2009-03-01 18:01 .sudo_as_admin_successful
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-01 17:49 Templates
drwx------  4 twistedghost twistedghost     4096 2009-03-03 10:55 .thumbnails
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-02 13:07 .update-manager-core
drwx------  2 twistedghost twistedghost     4096 2009-03-02 14:00 .update-notifier
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-03 03:36 Videos
drwxr-xr-x  3 twistedghost twistedghost     4096 2008-11-20 18:26 vuze
-rw-r--r--  1 twistedghost twistedghost 13521870 2009-03-02 18:20 Vuze_Installer.tar.bz2
drwxr-xr-x  4 twistedghost twistedghost     4096 2009-03-03 12:42 .wine
-rw-------  1 twistedghost twistedghost      131 2009-03-03 14:07 .Xauthority
drwx------  4 twistedghost twistedghost     4096 2009-03-02 13:44 .xchat2
drwxr-xr-x  2 twistedghost twistedghost     4096 2009-03-03 00:48 .xine
-rw-r--r--  1 twistedghost twistedghost    20998 2009-03-03 14:30 .xsession-errors
twistedghost@twistedghost-desktop:~$ /media/disk/home/twistedghost
bash: /media/disk/home/twistedghost: is a directory
twistedghost@twistedghost-desktop:~$

---

### Post by taurus on 2009-03-03
If you want to change to your old $HOME, you run

```
cd /media/disk/home/twistedghost
ls -la
```
Now, you can move whatever you want from old $HOME (/media/disk/home/twistedghost) to your new $HOME (/home/twistedghost).

---

### Post by TwistedGhost on 2009-03-03
ok so once i type that in is there some command that i have to use to transfer?

---

### Post by taurus on 2009-03-03
That is what I asked you earlier.  What do you want to copy and where do you want to copy to?

```
cp filename destination
```

---

### Post by TwistedGhost on 2009-03-03
i wnat to move the video and music files to my new partition and then delete the old partition

---

### Post by TwistedGhost on 2009-03-04
> **taurus said:**
> If you want to change to your old $HOME, you run

```
cd /media/disk/home/twistedghost
ls -la
```
Now, you can move whatever you want from old $HOME (/media/disk/home/twistedghost) to your new $HOME (/home/twistedghost).


twistedghost@twistedghost-desktop:/$ cd /media/disk/home/twistedghost
bash: cd: /media/disk/home/twistedghost: No such file or directory
twistedghost@twistedghost-desktop:/$

---

### Post by taurus on 2009-03-04
Did you mount your old partition?

```
sudo fdisk -l
df -h
```

---

### Post by TwistedGhost on 2009-03-04
twistedghost@twistedghost-desktop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8de8f9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18858   151476853+  83  Linux
/dev/sda2           18859       24321    43881547+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris
/dev/sda6           18859       23730    39134277   83  Linux
/dev/sda7           23731       23944     1718923+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 252 MB, 252968960 bytes
8 heads, 61 sectors/track, 1012 cylinders
Units = cylinders of 488 * 512 = 249856 bytes
Disk identifier: 0x058d058c

   Device Boot      Start         End      Blocks   Id  System
twistedghost@twistedghost-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              37G  7.0G   28G  20% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  212K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  652K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1             143G  137G     0 100% /media/disk
/dev/sda1             143G  137G     0 100% /home/twistedghost/oldstuff

---

### Post by taurus on 2009-03-04
> **TwistedGhost said:**
> twistedghost@twistedghost-desktop:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8de8f9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18858   151476853+  83  Linux
/dev/sda2           18859       24321    43881547+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris
/dev/sda6           18859       23730    39134277   83  Linux
/dev/sda7           23731       23944     1718923+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 252 MB, 252968960 bytes
8 heads, 61 sectors/track, 1012 cylinders
Units = cylinders of 488 * 512 = 249856 bytes
Disk identifier: 0x058d058c

   Device Boot      Start         End      Blocks   Id  System
twistedghost@twistedghost-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              37G  7.0G   28G  20% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  212K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  652K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile
[B][COLOR="Blue"]/dev/sda1             143G  137G     0 100% /media/disk
/dev/sda1             143G  137G     0 100% /home/twistedghost/oldstuff[/COLOR][/B]

```
cd /home/twistedghost/oldstuff
ls -la
```

---

### Post by TwistedGhost on 2009-03-04
new info

[http://pastebin.com/m1e690afd](http://pastebin.com/m1e690afd)

---

### Post by taurus on 2009-03-04
Try mounting the old / to /media/sda1 and keep the mount point the same instead of mounting that thing all over the place.  Makes it too confusing.

```
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
df -h
```

---

### Post by TwistedGhost on 2009-03-04
[http://pastebin.com/m76dc9e8e](http://pastebin.com/m76dc9e8e)

---

### Post by taurus on 2009-03-04
So your new $HOME (or the current one) is /home/twistedghost while your old $HOME is /media/sdb1/home/twistedghost.

```
ls -la /media/sdb1/home/twistedghost
```

---

### Post by TwistedGhost on 2009-03-04
twistedghost@twistedghost-desktop:~$ ls -la /media/sdb1/home/twistedghost
ls: cannot access /media/sdb1/home/twistedghost: No such file or directory
twistedghost@twistedghost-desktop:~$ sudo ls -la /media/sdb1/home/twistedghost
[sudo] password for twistedghost: 
ls: cannot access /media/sdb1/home/twistedghost: No such file or directory
twistedghost@twistedghost-desktop:~$

---

### Post by taurus on 2009-03-04
```
ls -la /media/sdb1
```

---

### Post by TwistedGhost on 2009-03-05
twistedghost@twistedghost-desktop:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              37G  6.9G   28G  20% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  208K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.9M  502M   1% /dev
tmpfs                 505M  588K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1             143G  133G  2.1G  99% /media/sda1
twistedghost@twistedghost-desktop:/$ 


twistedghost@twistedghost-desktop:~$ ls -la /media/sdb1
ls: cannot access /media/sdb1: No such file or directory
twistedghost@twistedghost-desktop:~$ ls
Desktop    Firefox_wallpaper.png  Pictures   Videos
Documents  Music                  Public     vuze
Examples   oldstuff               Templates  Vuze_Installer.tar.bz2
twistedghost@twistedghost-desktop:~$ cd ..
twistedghost@twistedghost-desktop:/home$ cd ..
twistedghost@twistedghost-desktop:/$ cd ..
twistedghost@twistedghost-desktop:/$ cd ..
twistedghost@twistedghost-desktop:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
boot   etc   initrd.img.old  media       proc  srv   usr  vmlinuz.old
cdrom  home  lib             mnt         root  sys   var
twistedghost@twistedghost-desktop:/$ ls -al
total 96
drwxr-xr-x  20 root root  4096 2009-03-02 13:09 .
drwxr-xr-x  20 root root  4096 2009-03-02 13:09 ..
drwxr-xr-x   2 root root  4096 2009-03-01 19:25 bin
drwxr-xr-x   3 root root  4096 2009-03-02 13:09 boot
lrwxrwxrwx   1 root root    11 2009-03-01 17:01 cdrom -> media/cdrom
drwxr-xr-x  16 root root 14480 2009-03-04 13:57 dev
drwxr-xr-x 137 root root 12288 2009-03-04 18:13 etc
drwxr-xr-x   7 root root  4096 2009-03-03 21:05 home
lrwxrwxrwx   1 root root    33 2009-03-02 13:09 initrd.img -> boot/initrd.img-2.6.27-11-generic
lrwxrwxrwx   1 root root    32 2009-03-01 17:33 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root 12288 2009-03-02 18:14 lib
drwx------   2 root root 16384 2009-03-01 17:01 lost+found
drwxr-xr-x   5 root root  4096 2009-03-04 18:13 media
drwxr-xr-x   2 root root  4096 2008-10-20 05:27 mnt
drwxr-xr-x   3 root root  4096 2009-03-02 18:23 opt
dr-xr-xr-x 140 root root     0 2009-03-04 13:20 proc
drwxr-xr-x  16 root root  4096 2009-03-04 13:11 root
drwxr-xr-x   2 root root  4096 2009-03-01 19:28 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 15:53 srv
drwxr-xr-x  12 root root     0 2009-03-04 13:20 sys
drwxrwxrwt  15 root root  4096 2009-03-04 14:23 tmp
drwxr-xr-x  11 root root  4096 2008-10-29 15:58 usr
drwxr-xr-x  15 root root  4096 2008-10-29 16:12 var
lrwxrwxrwx   1 root root    30 2009-03-02 13:09 vmlinuz -> boot/vmlinuz-2.6.27-11-generic
lrwxrwxrwx   1 root root    29 2009-03-01 17:33 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic

---

