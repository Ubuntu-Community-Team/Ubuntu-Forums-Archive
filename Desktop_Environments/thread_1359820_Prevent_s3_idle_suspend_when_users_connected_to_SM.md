---
title: "Prevent s3 idle suspend when users connected to SMB"
date: 2009-12-20
forum: Desktop Environments
---

### Post by Silas (son of Silas) on 2009-12-20
I have a PC running Karmic with a number of directories shared on my network using Samba.

The PC is set to suspend to RAM after 20 minutes of inactivity to save electricity, then I use WOL magic packets from clients to wake it from suspend as and when needed.

The problem I have is that it suspends when I am copying data to or from it via smb if it takes longer than 20 minutes.

Solution:

Schedule this script to run at the desired interval. If you need to stop suspends for a while, just create a file called suspend.lock and place it in the same directory as the script :
> 
#!/bin/bash

if [ -f suspend.lock ]
then
date
echo "Suspend aborted, restart lock file in place"
exit 1
fi

count=0

smbstatus > info.txt
grep "No locked files" info.txt > /dev/null

while [ "$?" != "0" ]
do
date #debug purposes, see if it actually is running
echo $count
echo "Locked files, waiting"
sleep 120
count=`expr $count + 1`

if [ $count = 8 ]
then
date
echo "Suspend aborted, too many attempts with locked files"
exit 2
fi
smbstatus > info.txt
grep "No locked files" info.txt > /dev/null
done

date
echo "Suspending Server"
pmi action suspend
exit 0


---

### Post by koekiemonster on 2010-03-06
i used your script as inspiration for my own suspend script, it uses python (i'm no bash expert ;) ) and also checks for local activity and XBMC playback.
[http://ubuntuforums.org/showthread.php?t=1423030](http://ubuntuforums.org/showthread.php?t=1423030)

---

### Post by Aikar on 2011-03-05
I also took inspiration from this and made my own because I dont think the script should be controlling the suspend, especially for a desktop you actually use.

So I wrote a script most people will be wanting instead, prevent the PC from going to sleep if shares active, when using the default Power Managements auto sleep feature.

[http://aikar.co/2011/03/03/ubuntu-prevent-sleep-samba/](http://aikar.co/2011/03/03/ubuntu-prevent-sleep-samba/)

This script will trick the OS into thinking a user is present when samba is active and only sleep when no file is actively in use.

It also differs from the OP in that it does not care if files are marked as locked but read only, as some read only entries are likely to show when a user simply has a folder open.

So this script will only prevent sleep when a file is actively in use over samba, as leaving a folder open on remote pc may keep a read only file lock, but you still want your PC to sleep in that case as no files are REALLY active.

edit: note:
Just as I wrote this I decided to run smbstatus...
It still lists a file locked from 14 hours ago when the PC that accessed it is sleeping. So you REALLY want to use my method of detection (looking for DENY_WRITE) instead of the OP's check for ANY locked files.

This desktop PC and the HTPC were both asleep last night yet a file is still listed on the smbstatus, so checking locked files is not reliable.

---

### Post by fredknex on 2011-11-22
So....what about 11.10? Unity breaks the sleep timer reset command

---

