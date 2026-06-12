---
title: "hdparm not putting HDD's to sleep"
date: 2010-12-12
forum: Desktop Environments
---

### Post by teeedubb on 2010-12-12
Hi all,

Im wanting to put HDD's to sleep using hdparm after 20min of activity (a 4x disk raid5 array and two single disks). I have edited /etc/hdparm.conf, adding the following lines at the end of the file:

```
#6TB RAID5 POWER DOWN

/dev/disk/by-id/scsi-SATA_ST32000542AS_5XW0T1R6 {
     spindown_time = 240
 }

/dev/disk/by-id/scsi-SATA_ST32000542AS_5XW0TJZ2 {
     spindown_time = 240
 }

/dev/disk/by-id/scsi-SATA_ST32000542AS_5XW0W8SR {
     spindown_time = 240
 }

/dev/disk/by-id/scsi-SATA_ST32000542AS_5XW0XM34 {
     spindown_time = 240
 }

#500GB DISK POWER DOWN

/dev/disk/by-id/scsi-SATA_SAMSUNG_HD501LJS0MUJDWQ411622 {
     spindown_time = 240
 }

/dev/disk/by-id/scsi-SATA_SAMSUNG_HD501LJS0MUJDWQ411623 {
     spindown_time = 240
 }

```If I issue the command (or variants of):

```
sudo hdparm -y /dev/disk/by-id/scsi-SATA_SAMSUNG_HD501LJS0MUJDWQ411622
```The HDD's will sleep with out issue. Ive looked around my log files and cant seem to find anything to do with hdparm, or the HDD's sleeping. Have I make a mistake in the .conf file? Is there some place hdparm logs, or if I can activate some sort of verbose mode? Or does hdparm need to be activated on boot?

Any help is greatly appreciated.

EDIT: I'm using ubuntu 10.04.1 x64 last updated today.

---

### Post by teeedubb on 2010-12-13
Just a note, all of these drives are for storage and are currently not used for anything.


I remembered that I had set the hdd's to spin down when possible in  the gnome power settings, Ive now turned that off but Im going to have  to wait a while to try it out as Im expanding an array.


 Ive also been thinking that I could add the individual hdparm  commands to load on boot, possibly by adding them to  /etc/gdm/Init/Default. Iirc, anything run in that script is  automatically granted root privileges, but Im not sure if its the best  way to do it, as I dont think the command will be issued until gdm  starts... but that shouldnt be a problem most of the time.


Any suggestions?

---

### Post by dabl on 2010-12-13
ext3 & ext4 filesystems have a default journalling "commit" frequency of every 5 seconds.  Every 5 seconds they sync metadata with data.  You can change the commit frequency, but it sounds like you want them to stay asleep until you manually wake them.  You'll probably have to unmount the drives to get them to stay asleep.

---

### Post by teeedubb on 2010-12-16
I solved the issue by adding the individual commands to /etc/rc.local. Everything works fine now, HDD's sleep as should. Dont know why it wouldn't work with the hdparm.conf... I haven't noticed the HDD's waking when they shouldn't, but I cant watch it all the time, its a shame that hdparm doesn't seem to log anywhere, this could come in handy trying to work out how long to put HDD's  sleep after.

Ive read about journaling messing with standy and life of HDD's, but I think that adding the -noatime option to the mount commands helps alleviate this issue. Every time Ive checked the HDD's they've been in standby mode, so maybe mounting the HDD's with palimpsest counters this issue? A log of HDD sleep/wake actions would come in handy here...

Is there anyway to view/create a log file loggin HDD sleep/wake events?

---

### Post by longestline on 2011-02-15
> Is there anyway to view/create a log file loggin HDD sleep/wake events?

you could set up an hourly cron that calls a shellscript with like 

hdparm -C /dev/sdb | sed -n 's/.*state is:\s.\(.*\)/\1/p'
(this gives you "active/idle" or "standby")
and add a datetime. hdparm -C of course doesn't wake up the drive.

---

### Post by teeedubb on 2011-02-26
Thanks for the tip!

---

