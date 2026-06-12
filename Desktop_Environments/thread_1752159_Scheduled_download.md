---
title: "Scheduled download"
date: 2011-05-07
forum: Desktop Environments
---

### Post by donpeter06 on 2011-05-07
Hi
i am using ubuntu 11.04 in my AMD machine,
I have scheduled some torrent and wget downloads using crontab and sleep commands respectively. Since the download starts at 2  AM i used to leave my system ON.  
I would like to know if the download will automatically start from the login screen itself.(That is suppose i switch ON the system at 2 AM and never bother to login to my account. )
Please help.

---

### Post by Krytarik on 2011-05-08
Out of my own experience, it does so.

Greetings.

---

### Post by mister_p_1998 on 2011-05-09
If no one is logged on at all nothing will run on a cron schedule, except maybe stuff for root. You need to set your pc to autologin, then run the jobs for a cron as your username. I do this every weekday. My PC wakes on alarm (23:30) then the cron jobs for Ktorrent, Hellanzb, Get_Iplayer Icepodder all start. The jobs are all killed by a cron job at 18:00 as my ISP measures bandwidth between 18:00 - 00:00, then the pc shuts down on a root cron job at 20:30. Then it all starts again the next day, I love cron!
Steve

---

### Post by donpeter06 on 2011-05-10
> **mister_p_1998 said:**
> If no one is logged on at all nothing will run on a cron schedule, except maybe stuff for root. You need to set your pc to autologin, then run the jobs for a cron as your username. I do this every weekday. My PC wakes on alarm (23:30) then the cron jobs for Ktorrent, Hellanzb, Get_Iplayer Icepodder all start. The jobs are all killed by a cron job at 18:00 as my ISP measures bandwidth between 18:00 - 00:00, then the pc shuts down on a root cron job at 20:30. Then it all stats again the next day, I love cron!
Steve
Looks Great
Thanx , 
could post the contents of your crontab here!!
I would like to see the syntax

---

### Post by mister_p_1998 on 2011-05-10
OK, Here you go: 
Its a bit long!!!


SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin

MAILTO=""
DISPLAY=DISPLAY=:0.0
Shell=SHELL=/bin/bash 
# Bandwidth Recorder (VNstat) 
0 6 * * 1,2,3,4,5	run-parts /etc/cron.daily

##### Ktorrent ####################################################################
# Ktorrent Weekdays
2 0 * * 1,2,3,4,5	export DISPLAY=:0 && /usr/bin/ktorrent

# Ktorrent Sunday
0 0 * * 7	export DISPLAY=:0 && /usr/bin/ktorrent

# Kill Ktorrent Weekdays
1 18 * * 1,2,3,4,5	killall ktorrent

# Kill Ktorrent Sunday
30 00 * * 7 killall ktorrent

##### Ted #########################################################################
# Ted Weekdays 
00 00,02,04,8,10,12,14,16 * * 1,2,3,4,5 export DISPLAY=:0 && /usr/bin/java -jar /home/steve/Ted-New/tedv09715/ted.jar

# Ted Sunday (Catchup Torrents)
01 00 * * 7 export DISPLAY=:0 && /usr/bin/java -jar /home/steve/Ted/tedv09715/ted.jar

# Kill Ted Sunday (Catchup Torrents)
29 00 * * 7 killall java

# Kill Java (TED) Weekdays
15 02,4,8,10,12,14,16,17 * * 1,2,3,4,5 killall java

# Kill Java (TED) Weekends
00,13 10,11,12,13,14,15,16,17,18,19,20,21 * * 7 killall java

##### Icepodder ##########################################################################
# Icepodder Weekdays
0 4,17 * * 1,2,3,4,5	export DISPLAY=:0 && /usr/bin/icepodder

# Kill Icepodder Weekdays
59 13,17 * * 1,2,3,4,5	killall python

### Hpodder Weekdays #############################################################################################

0 1,4,8,12,16 * * 1-5 /usr/bin/hpodder fetch >> /tmp/Hpodder.log

### Hpodder move and Rename Logfiles ############################################################################
30 16 * * 1-5 cp /tmp/Hpodder.log /home/steve/logs/incoming
31 16 * * 1-5 /home/steve/scripts/rename.sh

##### Miro #######################################################################

# Kill Miro
00 18 * * 1,2,3,4,5 killall miro.real
# Restart Gdesklets Weekdays
0,10 14,18 * * 1,2,3,4,5	export DISPLAY=:0 && /usr/bin/gdesklets

#### Kget ##########################################################################
# Kget Weekdays
# 15 03 * * 1,2,3,4,5 export DISPLAY=:0 && /usr/bin/kget

# Kill Kget Weekdays
00 18 * * 1,2,3,4,5 killall kget


##### Hellanzb #########################################################################
# Hellanzb Weekdays
02 0 * * 1-5 /usr/bin/hellanzb

# Kill Hellanzb Weekdays
59 17 * * 1-5 killall hellanzb

# Kill LottaNZB Weekdays ##########################################################################
00 18 * * 1-5 kill `ps aux | grep lotta | grep -v grep | awk '{print $2}'`

#### Dropbox ##########################################################################
30 04,12 * * 1,2,3,4,5 export DISPLAY=:0 && /home/steve/scripts/Dropbox.sh

# Kill Dropbox Weekdays
59 17 * * 1,2,3,4,5 killall dropbox

# Move Tidy up
00,45 19 * * 1-6 /home/steve/scripts/Move-Tidy-up.sh

# Newsbin Move ##########################################################################
00,05,10,15,20,30,40,45,50,55 * * * 1-7 mv -f /home/steve/Downloads/*.nzb /home/steve/.hellanzb/nzb/daemon.queue

# Move NZB's From Dropbox to Hellanzb Inbox #####################################################################
00,25,30,45,55 09,10,11,12,14,15,16 * * 1-5 mv -f /home/steve/Dropbox/Linux/NZB/*.nzb /home/steve/.hellanzb/nzb/daemon.queue

# Move Torrents from Dropbox to Torrents Inbox ################################################################
00,15,25,30,35,40,45,50,55 09,10,11,12,14,15,16 * * 1-5 mv -f /home/steve/Dropbox/Linux/NZB/*.torrent /storage/Storage/Torrents/TED

# Leechr ##########################################################################
00,30 * * * 1-7 /usr/bin/python /home/steve/leechr/leechr.py 2>>/tmp/Leechr.log
##### Get_Iplayer ##########################################################################

# Get_Iplayer Weekdays

45 00-17 * * 1-7 /home/steve/iplayer/Gip-batch.sh

#30 1-17 * * 1-7 /usr/bin/perl /home/steve/iplayer/gipaac2mp3 --type radio --modes flashaacstd --verbose --pvr 2>>/tmp/get_iplayer.log
#25 17 * * 1-7 rm /home/steve/.get_iplayer/radio.cache

# Move Get_iplayer WMA,AAC,M4A files to Conversion Folder (WMA)

# 30 15 * * 1-7 mv -f /home/steve/iplayer/*.wma /home/steve/iplayer/WMA
#15 15 * * 1-7 mv -f /home/steve/iplayer/*.aac /home/steve/iplayer/WMA 
#35 01-17 * * 1-7 mv -f /home/steve/iplayer/*.m4a /home/steve/iplayer/WMA

# Convert WMA Files to MP3

#45 16 * * 1-5 /usr/bin/soundconverter -b -m audio/mpeg -s .mp3 /home/steve/iplayer/WMA/*.wma
#15 16 * * 1-7 /usr/bin/soundconverter -b -m audio/mpeg -s .mp3 /home/steve/iplayer/WMA/*.aac 
#40 01,05,09,13,17 * * 1-7 /usr/bin/soundconverter -b -m audio/mpeg -s .mp3 /home/steve/iplayer/WMA/*.m4a

# Move Converted MP3 Files from WMA Folder Back to MP3 Folder & WMA Files to Processed
#50 17,18 * * 1-7 mv -f /home/steve/iplayer/WMA/*.mp3 /home/steve/iplayer
#45 18 * * 1-7 mv -f /home/steve/iplayer/WMA/*.wma /home/steve/iplayer/WMA/Processed
#55 18 * * 1-7 mv -f /home/steve/iplayer/WMA/*.aac /home/steve/iplayer/WMA/Processed 
#00 02,06,10,14,17,18 * * 1-7 mv -f /home/steve/iplayer/WMA/*.m4a /home/steve/iplayer/WMA/Processed

# Move Radio MP3's from Dropbox Folder to Iplayer
# 30 * * * 1-5 mv -f /home/steve/Dropbox/Linux/iplayer/#?.mp3 /home/steve/iplayer

# Move Get_Iplayer PVR's From Dropbox to Get_Iplayer Folder
59 * * * 1-5 mv -f /home/steve/Dropbox/Linux/iplayer/*.mp3 /home/steve/iplayer/pvr/
00 * * * 1-5 mv -f /home/steve/Dropbox/Linux/iplayer/* /home/steve/.get_iplayer/pvr/
00 19 * * 5 rm /home/steve/.dropbox/cache/*.*
40 17 * * 1-7 rm /home/steve/.get_iplayer/radio.cache

# Cron for Monthly VNstat Report ##########################################################################

08,55 18,19 28,30,31 * * /usr/bin/vnstat -i eth0 -m >/home/steve/logs/VNstat/incoming/Vnstat-Monthly-Report.txt

# Rename with Datestamp and Move VNstat log to Logs Folder ###################################################
01 00 1 * * /home/steve/scripts/rename-vnstat.sh

# 15,20,45,50,55 23,00 * * 6-7 /usr/bin/vnstat -i eth0 -m >/home/steve/Desktop/Vnstat-Monthly-Report.txt


Steve

---

### Post by donpeter06 on 2011-09-11
Thanx for the help

---

