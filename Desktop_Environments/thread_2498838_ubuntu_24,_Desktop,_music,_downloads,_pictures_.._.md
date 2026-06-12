---
title: "ubuntu 24, Desktop, music, downloads, pictures .. folders disappear"
date: 2024-06-30
forum: Desktop Environments
---

### Post by khalilxg on 2024-06-30
-so while using my ubuntu 24, i clicked onDesktop icon and i've got "oops something went wrong unable to find /home/Desktop please check the spelling or try again later"
- i reboot the laptop and found out i cant login, Msg password incorrect, tried to reset the password in recovery mode and i succeed, ---> relogin
- same behavior for other folders,
-the disk 500G exists with df-h
```
ubuntu@ubuntuu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           3.2G  2.9M  3.2G   1% /run
/dev/nvme0n1p2  468G  184G  261G  42% /
tmpfs            16G  140M   16G   1% /dev/shm
tmpfs           5.0M   12K  5.0M   1% /run/lock
efivarfs        192K  128K   60K  69% /sys/firmware/efi/efivars
tmpfs            16G     0   16G   0% /run/qemu
/dev/nvme0n1p1  511M  6.2M  505M   2% /boot/efi
tmpfs           3.2G  164K  3.2G   1% /run/user/1000
ubuntu@ubuntuu:~$
``` 


- ls -la not showing those folders,
```
ubuntu@ubuntuu:~$ ls -latotal 5884
drwxr-x--x 57 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   30 14:26 .
drwxr-xr-x  4 root   root      4096 &#1605;&#1575;&#1610;     3 15:11 ..
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 14:43 .5681250646225525941
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1605;&#1575;&#1585;&#1587;    8 15:48 .anaconda
-rw-rw-r--  1 ubuntu ubuntu     168 &#1580;&#1608;&#1575;&#1606;   24 00:30 .angular-config.json
drwxr-xr-x  2 ubuntu ubuntu    4096 &#1605;&#1575;&#1610;     5 13:18 .anydesk
-rw-rw-r--  1 ubuntu ubuntu      36 &#1580;&#1608;&#1575;&#1606;   12  2023 .bash_aliases
-rw-------  1 ubuntu ubuntu    4950 &#1580;&#1608;&#1575;&#1606;   30 14:26 .bash_history
-rw-------  1 ubuntu ubuntu   90480 &#1605;&#1575;&#1610;    10 23:00 .bash_history-07755.tmp
-rw-------  1 ubuntu ubuntu   93601 &#1605;&#1575;&#1610;     9 13:01 .bash_history-08984.tmp
-rw-------  1 ubuntu ubuntu       0 &#1605;&#1575;&#1610;     9 11:59 .bash_history-12384.tmp
-rw-------  1 ubuntu ubuntu   50706 &#1605;&#1575;&#1610;    29 01:39 .bash_history-17868.tmp
-rw-------  1 ubuntu ubuntu       0 &#1580;&#1608;&#1575;&#1606;   11 01:51 .bash_history-22185.tmp
-rw-------  1 ubuntu ubuntu       0 &#1605;&#1575;&#1610;    12 00:48 .bash_history-29454.tmp
-rw-------  1 ubuntu ubuntu       0 &#1605;&#1575;&#1610;    19 22:27 .bash_history-33958.tmp
-rw-------  1 ubuntu ubuntu       0 &#1605;&#1575;&#1610;    12 00:48 .bash_history-34172.tmp
-rw-------  1 ubuntu ubuntu       0 &#1601;&#1610;&#1601;&#1585;&#1610;  12 16:33 .bash_history-36866.tmp
-rw-------  1 ubuntu ubuntu  119610 &#1580;&#1575;&#1606;&#1601;&#1610;   4 14:52 .bash_history-39824.tmp
-rw-------  1 ubuntu ubuntu       0 &#1601;&#1610;&#1601;&#1585;&#1610;   7 14:17 .bash_history-55260.tmp
-rw-------  1 ubuntu ubuntu       0 &#1580;&#1608;&#1575;&#1606;   23 14:38 .bash_history-55360.tmp
-rw-------  1 ubuntu ubuntu       0 &#1605;&#1575;&#1610;    18 17:34 .bash_history-66143.tmp
-rw-------  1 ubuntu ubuntu   61006 &#1580;&#1608;&#1575;&#1606;   24 00:31 .bash_history-81150.tmp
-rw-------  1 ubuntu ubuntu   93770 &#1605;&#1575;&#1610;     9 00:47 .bash_history-95085.tmp
-rw-r--r--  1 ubuntu ubuntu     220 &#1580;&#1608;&#1575;&#1606;   12  2023 .bash_logout
-rw-r--r--  1 ubuntu ubuntu    5020 &#1605;&#1575;&#1610;    18 16:08 .bashrc
drwx------ 64 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   28 15:53 .cache
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;    9 23:29 .codeium
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;    1 15:36 .conda
-rw-rw-r--  1 ubuntu ubuntu      90 &#1580;&#1608;&#1575;&#1606;    1 15:21 .condarc
drwx------ 61 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   30 15:40 .config
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   17  2023 .continuum
drwxrwxr-x  5 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;    6 16:19 .dbclient
drwx------  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 15:21 .docker
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   17  2023 .dotnet
drwxr-xr-x  4 ubuntu ubuntu   45056 &#1580;&#1608;&#1575;&#1606;   29 18:04 Downloads
drwxrwxr-x  4 ubuntu ubuntu    4096 &#1605;&#1575;&#1585;&#1587;   10 18:40 .EasyOCR
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1606;&#1608;&#1601;&#1605;&#1576;&#1585; 15  2023 .electron-gyp
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1605;&#1575;&#1585;&#1587;    4 03:42 .fonts
-rw-rw-r--  1 ubuntu ubuntu     217 &#1605;&#1575;&#1610;    18 18:45 .gitconfig
drwx------  3 ubuntu ubuntu    4096 &#1587;&#1576;&#1578;&#1605;&#1576;&#1585; 20  2023 .gnome
drwx------  4 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   30 15:09 .gnupg
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 18:04 go
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1605;&#1575;&#1585;&#1587;    9 23:18 .gpac
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1580;&#1608;&#1610;&#1604;&#1610;&#1577; 30  2023 .gphoto
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1605;&#1575;&#1585;&#1587;    4 03:43 .insightface
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1606;&#1608;&#1601;&#1605;&#1576;&#1585; 24  2023 .ipynb_checkpoints
drwxrwxr-x  5 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   18  2023 .ipython
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1571;&#1603;&#1578;&#1608;&#1576;&#1585; 13  2023 .jupyter
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   18  2023 .keras
drwxr-xr-x  3 ubuntu    999    4096 &#1580;&#1608;&#1575;&#1606;   12  2023 .kube
-rw-rw-r--  1 ubuntu ubuntu     715 &#1571;&#1601;&#1585;&#1610;&#1604;   1 13:32 .labelImgSettings.pkl
-rw-------  1 ubuntu ubuntu      34 &#1580;&#1608;&#1575;&#1606;   29 20:33 .lesshst
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 18:04 llama.cpp
drwx------  6 ubuntu ubuntu    4096 &#1583;&#1610;&#1587;&#1605;&#1576;&#1585; 15  2023 .local
drwxrwxrwx  7 root   root      4096 &#1580;&#1608;&#1575;&#1606;   29 18:04 Mask_RCNN
drwx------  4 ubuntu ubuntu    4096 &#1605;&#1575;&#1610;    20 17:48 .mc
drwxr-xr-x 10 ubuntu ubuntu    4096 &#1580;&#1608;&#1610;&#1604;&#1610;&#1577; 18  2023 .minikube
drwx------  3 ubuntu ubuntu    4096 &#1605;&#1575;&#1610;    20 17:44 .minio
drwx------  3 ubuntu ubuntu    4096 &#1605;&#1575;&#1610;    15 13:27 .mongodb
drwx------  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   12  2023 .mozilla
-rw-------  1 ubuntu ubuntu       4 &#1580;&#1575;&#1606;&#1601;&#1610;  12 21:49 .node_repl_history
drwxrwxr-x  7 ubuntu ubuntu    4096 &#1605;&#1575;&#1610;    23 22:25 .npm
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1605;&#1575;&#1610;    23 22:32 .npm-packages
drwx------  3 ubuntu ubuntu    4096 &#1571;&#1608;&#1578;     7  2023 .nv
-rw-rw-r--  1 ubuntu ubuntu     449 &#1605;&#1575;&#1610;     5 01:12 .nvidia-settings-rc
drwxrwxr-x  8 ubuntu ubuntu    4096 &#1605;&#1575;&#1610;    23 22:43 .nvm
drwxr-xr-x  3 ubuntu ubuntu    4096 &#1601;&#1610;&#1601;&#1585;&#1610;  26 16:49 .ollama
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1605;&#1575;&#1585;&#1587;    4 03:52 .opennsfw2
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 19:17 Pictures
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   20  2023 .pip
drwx------  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   12  2023 .pki
-rw-r--r--  1 ubuntu ubuntu     843 &#1605;&#1575;&#1610;    19 21:25 .profile
-rw-------  1 ubuntu ubuntu     116 &#1605;&#1575;&#1610;    23 16:09 .psql_history
-rw-------  1 ubuntu ubuntu   26738 &#1580;&#1608;&#1575;&#1606;    2 00:12 .python_history
-rw-------  1 ubuntu ubuntu      34 &#1605;&#1575;&#1610;    17 22:42 .rediscli_history
drwxr-xr-x  2 ubuntu ubuntu    4096 &#1606;&#1608;&#1601;&#1605;&#1576;&#1585; 15  2023 .rpmdb
drwx------  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 19:17 snap
-rw-------  1 ubuntu ubuntu     127 &#1580;&#1608;&#1610;&#1604;&#1610;&#1577;  1  2023 .sqlite_history
drwx------  2 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 17:51 .ssh
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1583;&#1610;&#1587;&#1605;&#1576;&#1585; 22  2023 .streamlit
-rw-r--r--  1 ubuntu ubuntu       0 &#1580;&#1608;&#1575;&#1606;   12  2023 .sudo_as_admin_successful
-rw-r--r--  1 root   root   5097501 &#1580;&#1608;&#1575;&#1606;   30 15:42 testdisk.log
drwx------  6 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   12  2023 .thunderbird
drwxrwxr-x  2 ubuntu ubuntu    4096 &#1580;&#1608;&#1610;&#1604;&#1610;&#1577; 23  2023 .tuxcut
-rw-rw-r--  1 ubuntu ubuntu    5510 &#1605;&#1575;&#1610;    19 20:50 .v8flags.8.6.395.17-node.28.1d41c853af58d3a7ae54990ce29417d8.json
drwxr-xr-x  3 ubuntu ubuntu    4096 &#1583;&#1610;&#1587;&#1605;&#1576;&#1585; 12  2023 .var
-rw-------  1 ubuntu ubuntu    7436 &#1605;&#1575;&#1585;&#1587;   24 03:52 .viminfo
drwx------  5 ubuntu ubuntu    4096 &#1605;&#1575;&#1610;    14 23:04 .vnc
drwxrwxr-x  4 ubuntu ubuntu    4096 &#1605;&#1575;&#1610;    31 19:56 .vscode
drwxrwxr-x  4 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   17  2023 .vscode-insiders
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   25 19:59 .wdm
-rw-rw-r--  1 ubuntu ubuntu     423 &#1571;&#1601;&#1585;&#1610;&#1604;   2 14:11 .wget-hsts
drwxrwxr-x  3 ubuntu ubuntu    4096 &#1583;&#1610;&#1587;&#1605;&#1576;&#1585; 25  2023 .yarn
-rw-rw-r--  1 ubuntu ubuntu     116 &#1580;&#1608;&#1575;&#1606;   28 15:51 .yarnrc
ubuntu@ubuntuu:~$ 



```

-find cant find the folders
- editing [COLOR=#BDC1C6][FONT=Arial]~/.config/[/FONT][/COLOR][COLOR=#BCC0C3][FONT=Arial]**user**[/FONT][/COLOR][COLOR=#BDC1C6][FONT=Arial]-dirs.dirs  [/FONT][/COLOR], found out the paths are not existing 
```

"XDG_DESKTOP_DIR="$HOME/"XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/"
```



" i tried to rewrite the paths and reboot but the file return to None values like is the recent past "

if writing in  ~/.config/user-dirs.dirs , add just Desktop, then use  killall nautilus to proceed for solution.  ~/.config/user-dirs.dirs will be  ```
  GNU nano 7.2                   /home/ubuntu/.config/user-dirs.dirs                            # This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/"


but when i click on Desktop i got the error message" oops something went wrong check the spelling or try again", and also Desktop will not appear in ls nor ls -la, like adding Desktop to   ~/.config/user-dirs.dirs did nothing :(

```

- i dont have a restore plan 
- i have sensitive data they can't be lost
-all trying cases are followed with reboots etc, but the result is same "oops something went wrong check the spelling or try again" or folders not found

---

### Post by The Cog on 2024-06-30
Let's start by looking what disks you have, where they are mounted, and what should be mounted. Please can you try these commands, and post both the commands as you type them and their output here:
```
sudo mount -a
lsblk -fmp | grep -v snap
cat /etc/fstab
ls -l /home
ls -l ~
```

---

### Post by khalilxg on 2024-06-30
ubuntu@ubuntuu:~$ sudo mount -a
lsblk -fmp | grep -v snap
cat /etc/fstab
ls -l /home
ls -l ~
[sudo] password for ubuntu: 
NAME             FSTYPE   FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS                              SIZE OWNER GROUP MODE
/dev/nvme0n1                                                                                                                     476.9G root  disk  brw-rw----
&#9500;&#9472;/dev/nvme0n1p1 vfat     FAT32       355A-80B3                             504.8M     1% /boot/efi                                512M root  disk  brw-rw----
                                                                                          /                                                         
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=6e405ba9-a41b-4b47-9840-c0efb2fb677a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=355A-80B3  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
total 8
drwxr-xr-x  3 root   root   4096 &#1605;&#1575;&#1610;     3 15:11 linuxbrew
drwxr-x--x 57 ubuntu ubuntu 4096 &#1580;&#1608;&#1575;&#1606;   30 14:26 ubuntu
total 5028
drwxr-xr-x 4 ubuntu ubuntu   45056 &#1580;&#1608;&#1575;&#1606;   29 18:04 Downloads
drwxrwxr-x 3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 18:04 go
drwxrwxr-x 3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 18:04 llama.cpp
drwxrwxrwx 7 root   root      4096 &#1580;&#1608;&#1575;&#1606;   29 18:04 Mask_RCNN
drwxrwxr-x 3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 19:17 Pictures
drwx------ 3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 19:17 snap
-rw-r--r-- 1 root   root   5074519 &#1580;&#1608;&#1575;&#1606;   30 15:09 testdisk.log
ubuntu@ubuntuu:~$

---

### Post by khalilxg on 2024-06-30
[COLOR=#000000]ubuntu@ubuntuu:~$ sudo mount -a[/COLOR]
[COLOR=#000000]lsblk -fmp | grep -v snap[/COLOR]
[COLOR=#000000]cat /etc/fstab[/COLOR]
[COLOR=#000000]ls -l /home[/COLOR]
[COLOR=#000000]ls -l ~[/COLOR]
[COLOR=#000000][sudo] password for ubuntu:[/COLOR]
[COLOR=#000000]NAME FSTYPE FSVER LABEL UUID FSAVAIL FSUSE% MOUNTPOINTS SIZE OWNER GROUP MODE[/COLOR]
[COLOR=#000000]/dev/nvme0n1 476.9G root disk brw-rw----[/COLOR]
[COLOR=#000000]&#9500;&#9472;/dev/nvme0n1p1 vfat FAT32 355A-80B3 504.8M 1% /boot/efi 512M root disk brw-rw----[/COLOR]
[COLOR=#000000]/[/COLOR]
[COLOR=#000000]# /etc/fstab: static file system information.[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# Use 'blkid' to print the universally unique identifier for a[/COLOR]
[COLOR=#000000]# device; this may be used with UUID= as a more robust way to name devices[/COLOR]
[COLOR=#000000]# that works even if disks are added and removed. See fstab(5).[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# <file system> <mount point> <type> <options> <dump> <pass>[/COLOR]
[COLOR=#000000]# / was on /dev/nvme0n1p2 during installation[/COLOR]
[COLOR=#000000]UUID=6e405ba9-a41b-4b47-9840-c0efb2fb677a / ext4 errors=remount-ro 0 1[/COLOR]
[COLOR=#000000]# /boot/efi was on /dev/nvme0n1p1 during installation[/COLOR]
[COLOR=#000000]UUID=355A-80B3 /boot/efi vfat umask=0077 0 1[/COLOR]
[COLOR=#000000]/swapfile none swap sw 0 0[/COLOR]
[COLOR=#000000]total 8[/COLOR]
[COLOR=#000000]drwxr-xr-x 3 root root 4096 &#1605;&#1575;&#1610; 3 15:11 linuxbrew[/COLOR]
[COLOR=#000000]drwxr-x--x 57 ubuntu ubuntu 4096 &#1580;&#1608;&#1575;&#1606; 30 14:26 ubuntu[/COLOR]
[COLOR=#000000]total 5028[/COLOR]
[COLOR=#000000]drwxr-xr-x 4 ubuntu ubuntu 45056 &#1580;&#1608;&#1575;&#1606; 29 18:04 Downloads[/COLOR]
[COLOR=#000000]drwxrwxr-x 3 ubuntu ubuntu 4096 &#1580;&#1608;&#1575;&#1606; 29 18:04 go[/COLOR]
[COLOR=#000000]drwxrwxr-x 3 ubuntu ubuntu 4096 &#1580;&#1608;&#1575;&#1606; 29 18:04 llama.cpp[/COLOR]
[COLOR=#000000]drwxrwxrwx 7 root root 4096 &#1580;&#1608;&#1575;&#1606; 29 18:04 Mask_RCNN[/COLOR]
[COLOR=#000000]drwxrwxr-x 3 ubuntu ubuntu 4096 &#1580;&#1608;&#1575;&#1606; 29 19:17 Pictures[/COLOR]
[COLOR=#000000]drwx------ 3 ubuntu ubuntu 4096 &#1580;&#1608;&#1575;&#1606; 29 19:17 snap[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 5074519 &#1580;&#1608;&#1575;&#1606; 30 15:09 testdisk.log[/COLOR]
[COLOR=#000000]ubuntu@ubuntuu:~$[/COLOR]

---

### Post by oldfred on 2024-06-30
Please use code tags.
And go back and edit your posts above with each command, its output with code tags.
Easy to add code tags in Forum's Go Advanced Editor & # icon.

I cannot tell which command & which output is which.

Did you actually use ubuntu and ubuntuu as user & system name?
Default for live installer is ubuntu@ubuntu so getting confused if your system or live installer.

Post should look like this for mine, I have never edited this file:
```
[FONT=monospace][COLOR=#008000]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat ~/.config/user-dirs.dirs[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]# This file is written by xdg-user-dirs-update [/COLOR]
# If you want to change or add directories, just edit the line you're 
# interested in. All local changes will be retained on the next run. 
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped 
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an 
# absolute path. No other format is supported. 
#  
XDG_DESKTOP_DIR="$HOME/Desktop" 
XDG_DOWNLOAD_DIR="$HOME/Downloads" 
XDG_TEMPLATES_DIR="$HOME/Templates" 
XDG_PUBLICSHARE_DIR="$HOME/Public" 
XDG_DOCUMENTS_DIR="$HOME/Documents" 
XDG_MUSIC_DIR="$HOME/Music" 
XDG_PICTURES_DIR="$HOME/Pictures" 
XDG_VIDEOS_DIR="$HOME/Videos"
[/FONT]
```

---

### Post by khalilxg on 2024-06-30
```
ubuntu@ubuntuu:~$ sudo mount -alsblk -fmp | grep -v snap
cat /etc/fstab
ls -l /home
ls -l ~
[sudo] password for ubuntu: 
NAME             FSTYPE   FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS                              SIZE OWNER GROUP MODE
/dev/nvme0n1                                                                                                                     476.9G root  disk  brw-rw----
&#9500;&#9472;/dev/nvme0n1p1 vfat     FAT32       355A-80B3                             504.8M     1% /boot/efi                                512M root  disk  brw-rw----
                                                                                          /                                                         
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=6e405ba9-a41b-4b47-9840-c0efb2fb677a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=355A-80B3  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
total 8
drwxr-xr-x  3 root   root   4096 &#1605;&#1575;&#1610;     3 15:11 linuxbrew
drwxr-x--x 57 ubuntu ubuntu 4096 &#1580;&#1608;&#1575;&#1606;   30 14:26 ubuntu
total 9520
drwxr-xr-x 4 ubuntu ubuntu   45056 &#1580;&#1608;&#1575;&#1606;   29 18:04 Downloads
drwxrwxr-x 3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 18:04 go
drwxrwxr-x 3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 18:04 llama.cpp
drwxrwxrwx 7 root   root      4096 &#1580;&#1608;&#1575;&#1606;   29 18:04 Mask_RCNN
drwxrwxr-x 3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 19:17 Pictures
drwx------ 3 ubuntu ubuntu    4096 &#1580;&#1608;&#1575;&#1606;   29 19:17 snap
-rw-r--r-- 1 root   root   9672733 &#1580;&#1608;&#1575;&#1606;   30 15:56 testdisk.log
ubuntu@ubuntuu:~$ 






```

```

ubuntu@ubuntuu:~$ nano ~/.config/user-dirs.dirs
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/"










```

ubuntu= is name of user
ubuntuu= is name of laptop

we have ubuntu@ubuntuu:~$  AND  root@ubuntuu:~#

---

### Post by currentshaft on 2024-07-01
It is likely someone or something deleted those directories. Try looking at logs in /var/log to find out why.

---

### Post by khalilxg on 2024-07-01
same, this action have been done after exactly one hour of opening port 80 and 443 for testing deployments of my apps, nginx as reverse proxy for other opened local ports. Why that was fast and so brutal, deleting default ubuntu named folders, i dont know why ! i thought ubuntu is more secure shelter

---

### Post by khalilxg on 2024-07-01
i didnt even can to login even, after the first reboot, like how and why. user informations likke user password is gone, also the log is deleted

---

### Post by currentshaft on 2024-07-01
> **khalilxg said:**
> same, this action have been done after exactly one hour of opening port 80 and 443 for testing deployments of my apps, nginx as reverse proxy for other opened local ports. Why that was fast and so brutal, deleting default ubuntu named folders, i dont know why ! i thought ubuntu is more secure shelter

Well, did you expose these ports to the Internet, or only your secure local network?

---

### Post by khalilxg on 2024-07-01
on the internet, i port forward 80 and 443 on the router and opened 3001 and other ports on my computer ufw. i was testing my apps on pub network

---

### Post by currentshaft on 2024-07-01
> **khalilxg said:**
> on the internet, i port forward 80 and 443 on the router and opened 3001 and other ports on my computer ufw. i was testing my apps on pub network

Then unfortunately, it is very possible someone took advantage of your naivety and exploited your computer.

Disconnect the machine from the network and reinstall the operating system.

In the future, do not put unauthenticated services on the Internet, especially on well-known ports, and especially from systems which have something of value.

---

### Post by khalilxg on 2024-07-01
im already iin the step of reinstalling the os, any advice to safe deploy my apps from my ubuntu ? to pub network

---

