---
title: "[SOLVED] Can't mount /dev/sda4 as /home partition."
date: 2009-01-02
forum: General Help
---

### Post by utter-imadness on 2009-01-02
Hello.

I just finished installing Intrepid on my laptop. I already had a separate /home partition as /dev/sda4. During installation I told it to mount sda4 as my /home directory but the installation would always fail near the end. 
So I installed without mounting /sda4 as /home. I tried mounting it as home in ubuntu using 
```
$sudo mount /dev/sda4 /home
```
so when I go into GParted it says that /sda4 is my /home partition. But when I try to open Home it says that it opening it but it doesn't actually open. The weird thing is that I can still access it as a removable drive after unmounting it.

So how can I mount my /sda4 as /home considering what's happened so far?
Can this be due to incorrectly set up permissions?

---

### Post by taurus on 2009-01-02
Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by utter-imadness on 2009-01-02
Thanks.
```
imad@imad-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09e709e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         829     6658911   83  Linux
/dev/sda2   *       25125       29645    36314932+   7  HPFS/NTFS
/dev/sda3           29646       30401     6072570    5  Extended
/dev/sda4             830       25124   195149587+  83  Linux
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

```
imad@imad-laptop:~$ sudo blkid
/dev/sda1: UUID="1c2f38b1-00d4-4c45-b1df-973cfd808691" TYPE="ext3" 
/dev/sda2: UUID="3210569510565FC1" TYPE="ntfs" 
/dev/sda4: UUID="1da56650-dc3d-4d4a-bcdd-b155284c3898" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="6c7f6b86-9655-41b3-8f1d-9cd8699d3843"
```

```
imad@imad-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c2f38b1-00d4-4c45-b1df-973cfd808691 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c7f6b86-9655-41b3-8f1d-9cd8699d3843 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```
imad@imad-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             6.3G  2.7G  3.3G  45% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  104K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  240K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-7-generic/volatile
```

BTW, I currently do not have /sda4 mounted as /home. It is shown as a removable drive.

---

### Post by taurus on 2009-01-02
Is $HOME on /dev/sda4 is the same login name, imad, as you currently use?

All you need is to add an entry in /etc/fstab to have /dev/sda4 mount as /home.

```
UUID=1da56650-dc3d-4d4a-bcdd-b155284c3898   /home   ext3   defaults   0   2
```
Of course, you have to reboot after you've added that entry in for /dev/sda4.

---

### Post by utter-imadness on 2009-01-02
I tried something similar before: 
```
/dev/sda4 /home ext3 nodev,nosuid 0 2
```

When I rebooted it said that it couldn't find /home. I tried some recovery techniques but ended up reinstalling. 
Will this work for sure?

And yes, it's the same login name. And when I go to permissions it says that it is owned by 'root'.

---

### Post by taurus on 2009-01-02
Try mounting it somewhere and have a look at /dev/sda4 first.

```
sudo mkdir /media/sda4
sudo mount -t ext3 /dev/sda4 /media/sda4
ls -la /media/sda4
```
What's the output of the last command?

---

### Post by utter-imadness on 2009-01-02
```
imad@imad-laptop:~$ ls -la /media/sda4
total 32
drwxrwxrwx  5 root root  4096 2008-04-15 01:53 .
drwxr-xr-x  5 root root  4096 2009-01-02 11:40 ..
drwxrwxrwx 96  113 imad  4096 2009-01-01 22:44 imad
drwxrwxrwx  2 root root 16384 2008-12-06 21:38 lost+found
drwxrwxrwx  2 root root  4096 2008-12-17 15:13 $RECYCLE.BIN
```

---

### Post by taurus on 2009-01-02
> **utter-imadness said:**
> ```
imad@imad-laptop:~$ ls -la /media/sda4
total 32
drwxrwxrwx  5 root root  4096 2008-04-15 01:53 .
drwxr-xr-x  5 root root  4096 2009-01-02 11:40 ..
**[COLOR="Blue"]drwxrwxrwx 96  113 imad  4096 2009-01-01 22:44 imad[/COLOR]**
drwxrwxrwx  2 root root 16384 2008-12-06 21:38 lost+found
drwxrwxrwx  2 root root  4096 2008-12-17 15:13 $RECYCLE.BIN
```

The UID for imad is 113 while your UID (the default account on Ubuntu) is 1000.  You can see which UID for the current account is by running this command from a terminal.

```
id
```
What's the output of this command from a terminal?

```
ls -la /media/sda4/imad
```

---

### Post by utter-imadness on 2009-01-02
```
imad@imad-laptop:~$ id
uid=1000(imad) gid=1000(imad) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(imad)
```

```
imad@imad-laptop:~$ ls -la /media/sda4/imad
total 719080
drwxrwxrwx 96  113 imad      4096 2009-01-01 22:44 .
drwxrwxrwx  5 root root      4096 2008-04-15 01:53 ..
-rw-rw-rw-  1 imad imad       422 2008-11-23 11:51 2008-11-23-16-51-58.071-VirtualBox-15635.log
-rw-rw-rw-  1 imad imad       829 2008-09-28 12:34 .acidriprc
-rw-rw-rw-  1 imad imad       538 2008-09-28 11:12 acidrip.sh
drwxrwxrwx  3 imad imad      4096 2008-10-12 20:32 .adanaxis
drwxrwxrwx  3 imad imad      4096 2008-09-23 21:53 .adobe
drwxr-xr-x  7 imad imad      4096 2008-06-09 15:55 aircrack-ng-1.0-rc1
drwxrwxrwx  9 imad imad      4096 2008-10-15 16:20 .amsn
drwxrwxrwx  2 imad imad      4096 2008-10-15 16:19 .amsn_received
drwxrwxrwx  2 imad imad      4096 2008-11-16 09:58 .audacity1.3-imad
drwxrwxrwx  4 imad imad      4096 2008-11-16 09:58 .audacity-data
drwxrwxrwx  3 imad imad      4096 2008-10-06 16:43 .avidemux
drwx------ 10 imad imad      4096 2008-12-07 11:40 azumanga_daioh_v2
-rw-rw-rw-  1 imad imad     11591 2008-12-31 20:44 .bash_history
-rw-r--r--  1 imad imad       220 2009-01-01 22:44 .bash_logout
-rw-r--r--  1 imad imad      3115 2009-01-01 22:44 .bashrc
drwx------  6 imad imad      4096 2008-11-14 18:29 Bitter Virgin
-rw-rw-rw-  1 imad imad      2212 2008-12-05 11:50 .BOINC Manager
drwxr-xr-x  7 imad imad      4096 2008-12-06 13:49 .cache
-rw-rw-rw-  1 imad imad      2408 2008-11-29 23:14 client_state.xml
-rw-rw-rw-  1 imad imad     64974 2008-11-16 13:14 Colin.html
drwxrwxrwx  3 imad imad      4096 2008-09-24 00:01 .compiz
drwxr-xr-x 16 imad imad      4096 2009-01-01 22:44 .config
-rw-rw-rw-  1 imad imad         0 2008-10-22 18:30 .conkyrc
-rw-rw-rw-  1 imad imad      5081 2008-10-22 18:21 conkyrc.conf
drwxrwxrwx  3 root root      4096 2008-10-20 19:51 .dbus
drwxrwxrwx  3 imad imad      4096 2008-11-24 15:56 .designer
drwxr-xr-x 11 imad imad      4096 2008-12-31 20:47 Desktop
-rw-------  1 imad imad        28 2009-01-01 22:44 .dmrc
drwxr-xr-x  3 imad imad      4096 2008-11-12 09:51 Documents
drwxrwxrwx  2 imad imad      4096 2008-11-19 15:44 .DownloadManager
drwxrwxrwx 10 imad imad      4096 2008-11-28 16:08 .dvdcss
-rw-r--r--  1 imad imad      1319 2008-12-07 10:50 .dvdisaster
-rw-r--r--  1 imad imad        72 2008-12-07 10:49 .dvdisaster.log
drwxrwxrwx  2 imad imad      4096 2008-09-28 21:31 .dvdrip
drwxr-xr-x  3 imad imad      4096 2008-12-07 10:43 dvdrip-data
drwxrwxrwx  4 imad imad      4096 2008-09-28 21:31 .dvdrip-master
-rw-rw-rw-  1 imad imad     25766 2008-09-28 21:31 .dvdriprc
drwxr-xr-x  2 imad imad      4096 2008-09-29 17:10 dwhelper
-rw-r--r--  1 imad imad        56 2008-12-28 16:00 .easychemrc
drwxrwxrwx  5 imad imad      4096 2008-12-28 14:01 .elisa
-rw-------  1 imad imad        16 2009-01-01 22:44 .esd_auth
drwxrwxrwx  8 imad imad      4096 2008-12-31 15:57 .evolution
drwxrwxrwx  6 imad imad      4096 2008-12-31 10:12 .exaile
lrwxrwxrwx  1 imad imad        26 2009-01-01 22:44 Examples -> /usr/share/example-content
drwxrwxrwx  3 imad imad      4096 2008-12-28 18:08 .extcalc
drwxr-xr-x  2 imad imad      4096 2009-01-01 22:44 .fontconfig
drwxr-xr-x  5 imad imad      4096 2008-10-01 15:50 FrostWire
drwxrwxrwx  6 imad imad      4096 2008-12-06 19:17 .frostwire4.17
drwx------  6 imad imad      4096 2008-12-31 19:13 .gconf
drwx------  2 imad imad      4096 2009-01-02 10:28 .gconfd
drwxrwxrwx 22 imad imad      4096 2008-12-27 21:44 .gimp-2.4
drwxrwxrwx  2 imad imad      4096 2008-10-16 20:48 .giplet
-rw-r-----  1 imad imad         0 2009-01-01 22:44 .gksu.lock
drwx------ 23 imad imad      4096 2008-12-31 20:46 .gnome2
drwx------  2 imad imad      4096 2008-09-23 14:55 .gnome2_private
drwx------  2 imad imad      4096 2009-01-01 22:44 .gnupg
-rw-r--r--  1 root root         0 2008-12-11 13:50 go869224410682.pyget
drwxrwxrwx  3 imad imad      4096 2008-10-18 12:08 .google
drwxrwxrwx  6 imad imad      4096 2008-10-02 12:46 .googleearth
-rwx------  1 imad imad     15446 2008-12-07 13:33 gparted_details1.htm
-rwx------  1 imad imad      7158 2008-12-07 04:48 gparted_details.htm
drwxrwxrwx  2 imad imad      4096 2008-09-23 23:28 .gpilotd
-rw-rw-rw-  1 imad imad         5 2008-09-23 23:28 .gpilotd.pid
drwxr-xr-x  2 imad imad      4096 2009-01-01 22:44 .gstreamer-0.10
-rw-r--r--  1 imad imad       104 2009-01-01 22:44 .gtk-bookmarks
-rw-rw-rw-  1 imad imad        32 2008-11-29 23:14 gui_rpc_auth.cfg
drwx------  2 imad imad      4096 2008-09-23 14:55 .gvfs
-rw-------  1 imad imad       169 2009-01-01 22:44 .ICEauthority
drwxr-xr-x  2 imad imad      4096 2008-09-23 19:47 .icons
drwxr-x---  7 imad imad      4096 2008-10-16 19:11 .inkscape
-rw-rw-rw-  1 imad imad    436404 2008-10-10 12:20 ipodpatcher
drwxr-xr-x  4 imad imad      4096 2008-11-30 16:10 .java
drwx------  3 imad imad      4096 2008-09-23 23:55 .kde
drwx------  3 imad imad      4096 2008-12-07 10:18 .kde4
-rw-rw-rw-  1 imad imad         5 2008-09-24 16:03 .ktorrent.lock
-rw-rw-rw-  1 imad imad      9238 2008-02-02 18:27 libflashsupport_1.0~2219-1_i386.deb
-rw-rw-rw-  1 imad imad       151 2008-10-19 19:49 .lightyears.cfg
drwx------  3 imad imad      4096 2008-09-23 14:55 .local
-rw-rw-rw-  1 imad imad         0 2008-11-29 23:14 lockfile
drwxr-xr-x  3 imad imad      4096 2008-11-27 16:38 .lyrics
drwx------  3 imad imad      4096 2008-09-23 21:53 .macromedia
drwxr-xr-x  3 imad imad      4096 2008-09-24 14:04 .mcop
-rw-------  1 imad imad        31 2008-12-08 16:10 .mcoprc
drwx------  3 imad imad      4096 2008-09-23 14:55 .metacity
drwx------  5 imad imad      4096 2008-12-07 10:59 .mozilla
drwx------  3 imad imad      4096 2008-10-18 18:50 .mozilla-thunderbird
drwxr-xr-x  2 imad imad      4096 2008-11-30 13:07 .mplayer
drwxr-xr-x 47 imad imad      4096 2008-12-30 22:33 Music
-rw-rw-rw-  1 imad imad         0 2008-11-22 15:33 mypasswd1
drwxr-xr-x  4 imad imad     20480 2008-12-31 15:57 .nautilus
drwx------  2 imad imad      4096 2008-10-25 12:27 .nero
-rw-r--r--  1 imad imad      8459 2008-12-09 21:36 :) || £ | N!KÕL&#7854; || £ || :)2.html
-rw-rw-rw-  1 imad imad    111456 2008-11-09 21:11 :) || £ | N!KÕL&#7854; || £ || :).html
-rw-rw-rw-  1 imad imad         0 2008-11-21 18:43 NUL
-rw-rw-rw-  1 imad imad      1628 2008-12-21 23:06 .nvidia-settings-rc
drwx------  3 imad imad      4096 2008-12-21 18:42 .openoffice.org2
drwx------ 11 imad imad      4096 2008-12-31 13:22 .opera
-rw-rw-rw-  1 imad imad       186 2008-11-26 20:41 .ophcrackrc
drwxr-xr-x  4 imad imad      4096 2008-12-06 12:15 .orca
-rw-rw-rw-  1 imad imad         0 2008-10-10 11:08 Passphrase for wireless network BELL755.asc
drwxrwxrwx  5 imad imad      4096 2008-12-29 18:29 .penguintv
drwxr-xr-x 34 imad imad     20480 2008-12-28 23:21 Pictures
-rw-rw-rw-  1 imad imad    663400 2006-11-30 05:41 poweriso
-rw-rw-rw-  1 root root    293675 2006-12-03 11:00 poweriso.tar.gz
-rw-r--r--  1 imad imad       675 2009-01-01 22:44 .profile
drwxr-xr-x  2 imad imad      4096 2008-09-23 14:55 Public
drwxr-xr-x  2 imad imad      4096 2009-01-01 22:44 .pulse
-rw-------  1 imad imad       256 2009-01-01 22:44 .pulse-cookie
drwx------  6 imad imad      4096 2009-01-01 22:44 .purple
drwxr-xr-x  2 imad imad      4096 2008-12-08 16:08 .qt
drwxr-xr-x  2 imad imad      4096 2008-11-05 11:08 QuickStart
-rw-rw-rw-  1 imad imad     11308 2008-12-21 18:42 .recently-used
-rw-r--r--  1 imad imad    576162 2008-12-31 20:46 .recently-used.xbel
-rw-rw-rw-  1 imad imad       237 2008-12-06 13:51 .registry
drwxrwx---  3 imad imad      4096 2008-11-24 17:38 .sane
drwxr-xr-x 11 imad imad      4096 2008-08-30 12:21 sqlite-3.6.2
drwx------  2 imad imad      4096 2008-09-23 14:55 .ssh
drwxr-xr-x  3 imad imad      4096 2008-11-23 20:28 .subversion
-rw-r--r--  1 imad imad         0 2009-01-01 22:44 .sudo_as_admin_successful
drwxr-xr-x  4 imad imad      4096 2008-10-02 12:55 .sudoku
-rw-rw-rw-  1 imad imad     12288 2008-11-22 11:56 .swp
drwxr-xr-x  2 imad imad      4096 2008-09-23 14:55 Templates
drwxr-xr-x  2 imad imad      4096 2008-09-23 19:47 .themes
drwx------  5 imad imad      4096 2008-09-23 23:33 .thumbnails
drwx------  3 imad imad      4096 2008-10-18 18:48 .thunderbird
-rw-rw-rw-  1 imad imad         0 2008-11-29 23:14 time_stats_log
drwxr-xr-x  4 imad imad      4096 2008-10-04 10:13 .tomboy
-rw-rw-rw-  1 imad imad      5352 2008-10-04 10:13 .tomboy.log
drwxr-xr-x  5 imad imad      4096 2008-09-24 07:08 .transmission
drwx------  2 imad imad      4096 2008-11-12 10:17 .tsclient
-rwxr-xr-x  1  999  999 732766208 2008-12-31 21:44 ubuntu-8.10-desktop-i386.iso
drwxrwxrwx  3 imad imad      4096 2008-12-29 10:45 untitled folder
drwxr-xr-x  2 imad imad      4096 2009-01-01 22:44 .update-manager-core
drwx------  2 imad imad      4096 2008-09-24 22:17 .update-notifier
-rw-rw-rw-  1 root root        62 2008-12-06 11:36 .usb-creator.log
drwxr-xr-x  2 imad imad      4096 2008-12-04 19:02 Videos
drwxrwxrwx  4 imad imad      4096 2008-12-17 22:05 .VirtualBox
drwxr-xr-x  2 imad imad      4096 2008-11-15 20:26 VirtualBoxShare
drwxr-xr-x  3 imad imad      4096 2008-12-06 13:49 .vlc
drwx------  2 imad imad      4096 2008-09-24 22:01 .w3m
drwxr-xr-x  2 imad imad      4096 2008-12-28 16:37 .wapi
drwxrwxrwx  3 imad imad      4096 2008-12-29 12:52 .wengophone
drwxr-xr-x  4 imad imad      4096 2008-12-31 20:16 .wine
drwxrwxrwx  2 imad imad      4096 2008-12-14 16:21 .wireshark
-rw-------  1 imad imad       122 2009-01-01 22:44 .Xauthority
drwx------  3 imad imad      4096 2008-12-31 20:46 .xchat2
drwxr-xr-x  2 imad imad      4096 2008-12-08 16:08 .xine
-rw-rw-rw-  1 imad imad       146 2008-12-04 16:07 .xscreensaver-getimage.cache
-rw-r--r--  1 imad imad      3514 2009-01-01 22:44 .xsession-errors
```

---

### Post by taurus on 2009-01-02
You need to change the UID and permissions of imad on /dev/sda4.

```
sudo chown -R 1000:1000 /media/sda4/imad
sudo chmod 755 /media/sda4/imad
```
Then, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda4   /home   ext3   **defaults**   0   2
```
Save it and reboot.

---

### Post by utter-imadness on 2009-01-02
That worked like a charm! Thank you very much!:KS

---

### Post by Schok on 2009-01-02
hey i followed the guide in this link. worked for me..tho i did mess up a bit somewhere in the middle..lol

[http://www.go2linux.org/how-to-move-home-directory-to-another-partition](http://www.go2linux.org/how-to-move-home-directory-to-another-partition)

---

