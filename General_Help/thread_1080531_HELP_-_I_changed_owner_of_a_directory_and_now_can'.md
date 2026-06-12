---
title: "HELP - I changed owner of a directory and now can't log in"
date: 2009-02-25
forum: General Help
---

### Post by emarkay on 2009-02-25
Don't ask - but in GK SUDO NAUTILUS I changed a directory to my username, , and then I think I inadvertently did the same to my HOME directory.

(I was trying to get a WINE program to work and I forgot I was in ROOT access)


Anyways when I boot, I get the login window but no mouse or keyboard inputs.

Using the live CD, I can see  my user directories, but they are all owned by "1000", and I can't even get to my data (my thunderbird emails for example - to copy in case I need to reload Ubuntu) - they are all just showing the "lock" and no data inside the folder.

I know I really should have investigated further but can anyone help - CHMOD or something like that???

HELP!

THANKS!

---

### Post by taurus on 2009-02-25
I thought the first regular user on the system has an UID 1000!

Boot into recover mode from GRUB menu and get to the root shell.  Then, post the outputs of these commands.

```
ls -la /home
tail /etc/passwd
```

---

### Post by emarkay on 2009-02-25
Sorry it took so long - had to wait for the cive CD to boot...

That's a lot of data there - is there a way to send output of a command to a file - I recall it was "pipelining" in DOS...

DRWXRWXR_X  3 root root .
DRWXRWXRWX  20 <username> ..
DRWXRWXRWX  53 <username> <usermane>

All the next entries end in "BIN/FASLE" except
<username> ,,,:/home/ <usermname>: /bin/bash


Thanks

---

### Post by taurus on 2009-02-25
If you are running from Ubuntu LiveCD, mount the partition where / is (unless you have a separate /home).  Then post the outputs of these commands.

Assuming / is located on /dev/sda1, do

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
ls -la /media/ubuntu/home
tail /media/ubuntu/etc/passwd
```

---

### Post by emarkay on 2009-02-25
When I installed it originally, I used the default directory information - I didn't specify anything except a Swap file.

Not being paranoid, but anything with "assuming" is scary. 

My Linux is on a shared Windows system - let me get my Gparted disc to find out what "SDX" my linux is on - I KNEW  I should have saved all this when I installed it...

[kicking myself intently]

---

### Post by taurus on 2009-02-25
> **emarkay said:**
> When I installed it originally, I used the default directory information - I didn't specify anything except a Swap file.

Not being paranoid, but anything with "assuming" is scary. 

**My Linux is on a shared Windows system** - let me get my Gparted disc to find out what "SDX" my linux is on - I KNEW  I should have saved all this when I installed it...

[kicking myself intently]

You mean wubi!

```
sudo fdisk -l
```

---

### Post by emarkay on 2009-02-25
Cool - I remembered there's a "Partition Editor"

it's SDB1 (/media/disk) and SDB2 for the SWAP

Let me run the commands now.

---

### Post by emarkay on 2009-02-25
ls -la /media/ubuntu/home

total 12
drwxrwxr-x  3 root root 4096 2009-02-15 19:17 .
drwxrwxrwx 20 1000 1000 4096 2009-02-16 15:36 ..
drwxrwxrwx 53 1000 1000 4096 2009-02-25 18:43 emarkay
ubuntu@ubuntu:~$ 

tail /media/ubuntu/etc/passwd
ubuntu@ubuntu:~$ tail /media/ubuntu/etc/passwd
tail: cannot open `/media/ubuntu/etc/passwd' for reading: Permission denied
ubuntu@ubuntu:~$ 

Gimmee a sec....

---

### Post by emarkay on 2009-02-25
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917        9398    44034165    7  HPFS/NTFS
/dev/sda3            9399        9726     2634660    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f041460

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6654    53448223+  83  Linux
/dev/sdb2            6655        7012     2875635   82  Linux swap / Solaris
/dev/sdb3            7013       19457    99964462+   7  HPFS/NTFS

---

### Post by taurus on 2009-02-25
Use the sudo with the tail.

```
sudo tail /media/ubuntu/etc/passwd
```

---

### Post by emarkay on 2009-02-25
"You do not have the permissions necessary to open the file."
/media/ubuntu/etc/passwd

Let me try more avenues...

---

### Post by emarkay on 2009-02-25
sudo tail /media/ubuntu/etc/passwd


   1. You have included 12 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

OOPs...

---

### Post by emarkay on 2009-02-25
pulse:x:106:115:PulseAudio daemon,,,:/var/run/pulse:/bin/false
saned:x:107:118::/home/saned:/bin/false
messagebus:x:108:119::/var/run/dbus:/bin/false
polkituser:x:109:120:PolicyKit,,,:/var/run/PolicyKit:/bin/false

---

### Post by emarkay on 2009-02-25
Damn emoticons>>>>>

---

### Post by emarkay on 2009-02-25
haldaemon:x:111:122:Hardware abstraction layer,,,:/var/run/hald:/bin/false
emarkay:x:1000:1000:emarkay,,,:/home/emarkay:/bin/bash
ntp:x:112:125::/home/ntp:/bin/false
clamav:x:114:128::/var/lib/clamav:/bin/false
boinc:x:113:126:BOINC core client,,,:/var/lib/boinc-client:/bin/false

---

### Post by emarkay on 2009-02-25
avahi:x:110:121:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false

between the two.

---

### Post by emarkay on 2009-02-25
screencap:

---

### Post by taurus on 2009-02-25
> **emarkay said:**
> ls -la /media/ubuntu/home

total 12
drwxrwxr-x  3 root root 4096 2009-02-15 19:17 .
drwxrwxrwx 20 1000 1000 4096 2009-02-16 15:36 ..
drwxrwxrwx 53 1000 1000 4096 2009-02-25 18:43 emarkay
ubuntu@ubuntu:~$ 


First, .. (/home) should own by root and your $HOME should have permissions of at least 755--read/write/executable for owner, read/executable for group, and read/executable for world.

```
sudo chown root /media/ubuntu/home
sudo chmod 755 /media/ubuntu/home
sudo chmod 755 /media/ubuntu/home/emarkay
```
Now, look at the ownerships and file permissions of your own $HOME.

```
ls -la /media/ubuntu/home/emarkay
```

---

### Post by emarkay on 2009-02-25
total 364
drwxr-xr-x  53 1000 1000  4096 2009-02-25 18:43 .
drwxr-xr-x   3 root root  4096 2009-02-15 19:17 ..
drwx------   3 1000 1000  4096 2009-02-16 04:53 .adobe
drwxrwxr-x   2 1000 1000  4096 2009-02-21 02:23 .audacity1.3-emarkay
drwxrwxr-x   7 1000 1000  4096 2009-02-21 02:23 .audacity-data
drwxrwxrwx   2 1000 1000  4096 2009-02-15 20:32 BACKUPS
-rw-------   1 1000 1000   579 2009-02-25 18:07 .bash_history
-rwxrwxr-x   1 1000 1000   220 2009-02-15 19:17 .bash_logout
-rwxrwxr-x   1 1000 1000  3115 2009-02-15 19:17 .bashrc
drwxr-xr-x   2 1000 1000  4096 2009-02-16 02:10 BOINC
-rw-r--r--   1 1000 1000  1905 2009-02-21 02:24 .BOINC Manager
drwxr-xr-x   4 1000 1000  4096 2009-02-16 05:27 .cache
drwx------   3 1000 1000  4096 2009-02-15 19:57 .compiz
drwxrwxr-x   9 1000 1000  4096 2009-02-25 17:37 .config
drwxrwxr-x   3 1000 1000  4096 2009-02-15 19:22 .dbus
drwxrwxrwx   2 1000 1000  4096 2009-02-25 17:42 Desktop
-rw-------   1 1000 1000    28 2009-02-25 17:41 .dmrc
drwxrwxrwx   2 1000 1000  4096 2009-02-25 18:43 DOCUMENTS
drwxr-xr-x   3 1000 1000  4096 2009-02-25 18:10 DOWNLOADS
drwxrwxrwx   2 1000 1000  4096 2009-02-17 16:10 EBAY IMAGES
-rw-r-----   1 1000 1000   128 2009-02-16 02:00 edid.bin
-rwxrwx--x   1 1000 1000    16 2009-02-15 19:22 .esd_auth
drwxr-xr-x   7 1000 1000  4096 2009-02-15 20:53 .evolution
lrwxrwxrwx   1 1000 1000    26 2009-02-15 19:17 Examples -> /usr/share/example-content
drwxrwxrwx   4 1000 1000  4096 2009-02-15 20:32 Extra FONTS
drwxrwxr-x   2 1000 1000  4096 2009-02-16 06:14 .fontconfig
drwxrwxr-x   5 1000 1000  4096 2009-02-25 18:05 .gconf
drwxrwxr-x   2 1000 1000  4096 2009-02-25 18:43 .gconfd
drwxrwxr-x   4 1000 1000  4096 2009-02-16 06:13 .gegl-0.0
drwxrwxr-x  22 1000 1000  4096 2009-02-16 06:14 .gimp-2.6
-rw-r-----   1 1000 1000     0 2009-02-25 18:06 .gksu.lock
drwxrwxr-x  10 1000 1000  4096 2009-02-25 18:43 .gnome2
drwxrwxr-x   2 1000 1000  4096 2009-02-15 19:22 .gnome2_private
drwxrwxr-x   2 1000 1000  4096 2009-02-16 21:37 .gnupg
drwxr-xr-x   2 1000 1000  4096 2009-02-16 05:26 .gstreamer-0.10
-rw-r--r--   1 1000 1000   116 2009-02-25 18:42 .gtk-bookmarks
drwx------   2 1000 1000  4096 2009-02-15 19:22 .gvfs
-rwx--x--x   1 1000 1000  4425 2009-02-25 18:05 .ICEauthority
drwxr-xr-x   2 1000 1000  4096 2009-02-16 00:29 .icons
drwxrwxrwx   2 1000 1000  4096 2009-02-15 20:32 IMAGES FOR LINUX
drwx------   3 1000 1000  4096 2009-02-15 19:22 .local
drwx------   3 1000 1000  4096 2009-02-16 04:53 .macromedia
drwx------   4 1000 1000  4096 2009-02-15 19:42 .mozilla
drwxr-xr-x   3 1000 1000  4096 2009-02-16 00:29 MOZILLA_FIREFOX_BETA
drwx------   3 1000 1000  4096 2009-02-15 19:42 .mozilla-thunderbird
drwxrwxrwx   2 1000 1000  4096 2009-02-16 05:39 MRK Drawings
drwxrwxrwx 110 1000 1000  4096 2009-02-25 16:44 MRK Images
drwxrwxrwx   8 1000 1000  4096 2009-02-15 20:42 MRK Internet files
drwxrwxrwx   2 1000 1000  4096 2009-02-16 05:51 MRK Sounds
drwxr-xr-x   2 1000 1000 36864 2009-02-16 21:58 MRK Videos
drwxr-xr-x   3 1000 1000  4096 2009-02-25 18:43 .nautilus
-rw-r--r--   1 1000 1000  1071 2009-02-16 02:00 .nvidia-settings-rc
drwxrwxr-x   3 1000 1000  4096 2009-02-23 01:01 .openoffice.org2
drwxrwxrwx   2 1000 1000  4096 2009-02-15 20:32 Pictures
-rwxrwxr-x   1 1000 1000   675 2009-02-15 19:17 .profile
drwxrwxr-x   2 1000 1000  4096 2009-02-15 19:23 .pulse
-rwxrwx--x   1 1000 1000   256 2009-02-15 19:22 .pulse-cookie
-rw-------   1 1000 1000  1460 2009-02-23 01:01 .recently-used
-rw-------   1 1000 1000 25057 2009-02-25 18:43 .recently-used.xbel
drwxrwxrwx   2 1000 1000  4096 2009-02-15 20:42 SHARED
drwxrwxr-x   2 1000 1000  4096 2009-02-16 21:37 .ssh
-rw-r--r--   1 1000 1000     0 2009-02-15 19:23 .sudo_as_admin_successful
drwxrwxrwx   2 1000 1000  4096 2009-02-15 20:42 TEMP
drwxr-xr-x   2 1000 1000  4096 2009-02-15 19:25 .themes
drwx------   3 1000 1000  4096 2009-02-15 19:25 .thumbnails
drwxrwxrwx   6 1000 1000  4096 2009-02-15 20:33 TORN
drwxr-xr-x   2 1000 1000  4096 2009-02-15 19:28 .update-manager-core
drwx------   2 1000 1000  4096 2009-02-15 19:23 .update-notifier
-rw-r--r--   1 1000 1000     2 2009-02-25 17:14 .windows-serial
drwxrwxr-x   4 1000 1000  4096 2009-02-25 18:14 .wine
drwxrwxr-x   2 1000 1000  4096 2009-02-25 17:12 WINEDOWNLOADS
-rw-------   1 1000 1000   126 2009-02-25 17:41 .Xauthority
--wx--x--x   1 1000 1000 27807 2009-02-25 18:43 .xsession-errors
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-02-25
Go ahead and reboot.  See if you can log in with your username, emarkay, and password.

---

### Post by emarkay on 2009-02-25
Nope - no mouse activity no keyboard activity.

---

### Post by emarkay on 2009-02-25
I can't mount the Volume in Nautilus (to get to the data) and I can't get to "computer" in GKSUDO NAUTILUS...

Grrrrr...

And MOZILLA THUNDERBIRD is still owned by "1000" - but it's not a "Lock" it's a "Crosshair" now.

---

### Post by emarkay on 2009-02-25
How can I just get root access to everything?  I am going to reload completely (format and all) all I need is my emails in Thunderbird - everything else is backed up.

I can "Copy" the directory but can't pacte it (on a CD-ROM for example...) :

"The folder ".mozilla-thunderbird" cannot be handled because you do not have permissions to read it."

---

### Post by apmcd47 on 2009-02-25
> **emarkay said:**
> How can I just get root access to everything?  I am going to reload completely (format and all) all I need is my emails in Thunderbird - everything else is backed up.

I can "Copy" the directory but can't pacte it (on a CD-ROM for example...) :

"The folder ".mozilla-thunderbird" cannot be handled because you do not have permissions to read it."

Can you get to a command line login, using CTRL-ALT-F1? If so, can you login as yourself or as root? If you can login as yourself you should be able to get a root shell (sudo su? sudo bash?).
If not, reboot and hit the escape key at the Grub prompt, then select recovery mode. On my system I can enter "single user mode", but I have set the root password. If you haven't set a root password it will either let you straight in as root or go onto a full reboot.

Andrew

---

### Post by emarkay on 2009-02-25
I don't know how, but this time: 

gksudo nautilus 

allowed me to change the owner from "1000" to "ubuntu live user" 

and I was able to copy my emails to a CD - Now I am going to reinstall a CLEAN UBUNTU.

I REALLY NEED TO STOP MESSING WITH THINGS THAT I DON'T KNOW 100% ABOUT.

(All I was doing was trying to get my Irfanview working in Ubunti again)

THANK YOU!!!!!!!!!

MRK

---

