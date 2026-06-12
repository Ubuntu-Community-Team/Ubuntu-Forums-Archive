---
title: "What's wrong with my back_up script?"
date: 2009-01-11
forum: General Help
---

### Post by sn0m on 2009-01-11
Oh Dear, here we go again.
I have a lap top and its main hard drive is dived in 4 partitions, one swap, another ext3 for ubuntu, one ntfs for xp and last one ntfs as main file holder for both xp and linux.
The reason why I keep xp is that aI can't sync my pda with linux.
Anyway, there's a folder with my scripts in home directory which I like to back up periodically from cron and my pda documents folder in xp that I also would like to back up periodically from cron.
So I wrote a script which looks like this:

#!/bin/sh
#script to back up documents
#Variables
DATE=`date +%d-%B-%Y`
FILE1=/home/sn0m/my_scripts
FILE2=/home/sn0m/main_disk/backup_linux/my_scripts_backup
FILE3=/home/sn0m/xp_disk/Documents\ and\ Settings/Administrator/My\ Documents/WM_kroksi_krook\ My\ Documents
FILE4=/home/sn0m/main_disk/backup_xp/pda_files_backup
#------------------------------------------------------------------------------
/bin/mount -t ntfs /dev/sda4 /home/sn0m/main_disk
#-------------------------------------------------------------------------------------
/bin/mount -t ntfs /dev/sda3 /home/sn0m/xp_disk
#----------------------------------------------------------------------------
#change to my_script folder
cd $FILE1
/bin/cp -u -r * $FILE2
#change to pda files
cd $FILE3
/bin/cp * $FILE4
cd /home/sn0m
#unmount backup drives
/bin/umount -f main_disk xp_disk

#end

It seems to copy all my scripts and directories inside to $FILE2 but nothing for pda files and I get this message from bash:

sn0m@sn0m-laptop:~/my_scripts$ sudo ./back_up.sh 
/bin/cp: cannot stat `*': No such file or directory
sn0m@sn0m-laptop:~/my_scripts$ 

What am I doing wrong here????
All help appreciated
Sokol

---

### Post by lswb on 2009-01-11
My guess is that you are running this script as a regular user and don't have permissions to do the mounts. I would suggest mounting the ntfs partitions in /etc/fstab with appropriate permissions so that you don't need to mount them in the script.

---

### Post by b0b138 on 2009-01-11
I think you have a line that doesn't look right.

.....ator/My\ Documents/WM_kroksi_krook**[COLOR="Red"]\ M[/COLOR]**y\ Documents

.....ator/My\ Documents/WM_kroksi_krook/My\ Documents

---

