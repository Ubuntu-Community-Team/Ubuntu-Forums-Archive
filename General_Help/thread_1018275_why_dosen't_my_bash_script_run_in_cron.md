---
title: "why dosen't my bash script run in cron"
date: 2008-12-21
forum: General Help
---

### Post by sn0m on 2008-12-21
Hi 
I have written a bash script to record live stream using mplayer.
The script is as follows:

#!/bin/bash
# a simple script to capture 2 hr of tar 
mplayer -vc null -vo null -ao pcm:fast:waveheader:file=tar.wav "http://tar.serverroom.us:9078/" &
# the & sets the job running in the background
sleep 30s
kill $! # kill the most recently backgrounded job
------------------------------------------------------
#improve sound quality and volume using sox
sox tar.wav -n stat > stats 2>&1 || exit 1
VOL=$(grep 'Volume' stats | sed 's/^.*[ \t]//')
sox -v $VOL tar.wav tari.wav || exit 1
rm tar.wav
------------------------------------------------------
#convert to mp3
for i in *.wav; do
 if [ -e "$i" ]; then
   tar=`basename "$i" .wav`
   lame -h -b 192 "$i" "$tar.mp3"
 fi
done
#need to clear up
rm *.wav stats
#end


it is saved as mpl_tar_experiment.sh in my home folder and I have given it executing powers with chmod 0755 and it works a charm when ./mpl_tar_experiment.sh

just to be sure 

ls -l  gives -rwxr-xr-x 1 sn0m sn0m   723 2008-12-22 03:54 mpl_tar_experiment.sh


So my next step was to make it run at particular time in crontab.
So edited my crontab -e and it looks like this:

sn0m@sn0m-laptop:~$ crontab -l
# m h  dom mon dow   command

#exp script

* * * * * /home/sn0m/mpl_tar_experiment.sh
                       

#
                                      
sn0m@sn0m-laptop:~$ 

I'm sure cron is running it as when i do:

sn0m@sn0m-laptop:~$ ps aux | grep mpl_tar_experiment.sh
sn0m      9440  0.0  0.0   1844   492 ?        Ss   04:19   0:00 /bin/sh -c /home/sn0m/mpl_tar_experiment.sh
sn0m      9441  0.0  0.0   4352  1480 ?        S    04:19   0:00 /bin/bash /home/sn0m/mpl_tar_experiment.sh
sn0m      9519  0.0  0.0   3240   812 pts/1    S+   04:19   0:00 grep mpl_tar_experiment.sh
sn0m@sn0m-laptop:~$ ps aux | grep mpl_tar_experiment.sh
sn0m      9559  0.0  0.0   1844   488 ?        Ss   04:20   0:00 /bin/sh -c /home/sn0m/mpl_tar_experiment.sh
sn0m      9561  0.0  0.0   4352  1476 ?        S    04:20   0:00 /bin/bash /home/sn0m/mpl_tar_experiment.sh
sn0m      9724  0.0  0.0   3240   816 pts/1    S+   04:20   0:00 grep mpl_tar_experiment.sh
sn0m@sn0m-laptop:~$ 


also on reading syslog file:

Dec 22 04:19:01 sn0m-laptop /USR/SBIN/CRON[9440]: (sn0m) CMD (/home/sn0m/mpl_tar_experiment.sh)
Dec 22 04:20:00 sn0m-laptop kernel: [ 1226.984139] CE: hpet increasing min_delta_ns to 15000 nsec
Dec 22 04:20:01 sn0m-laptop /USR/SBIN/CRON[9559]: (sn0m) CMD (/home/sn0m/mpl_tar_experiment.sh)
Dec 22 04:20:01 sn0m-laptop /USR/SBIN/CRON[9567]: (root) CMD (/home/sn0m/bin/exp                          )
Dec 22 04:21:01 sn0m-laptop /USR/SBIN/CRON[9763]: (sn0m) CMD (/home/sn0m/mpl_tar_experiment.sh)
Dec 22 04:22:01 sn0m-laptop /USR/SBIN/CRON[9891]: (sn0m) CMD (/home/sn0m/mpl_tar_experiment.sh)

so the cron is runign the script but it is not executing????? Any help to what is actually the problem here?

Thanks in advance
Sokol

---

### Post by dagnabit dang doohickey on 2008-12-21
Ambiguous file paths when run as cron job.

---

### Post by bodhi.zazen on 2008-12-21
cron is a very limited shell, so you have to use the full path for executables in your script and to your script.

ie /bin/sleep rather the sleep

To make life easier, you can set a variable in your scipt

SLEEP='/bin/sleep'

Then you can call it with $SLEEP rather then typing /bin/sleep over and over.

IMO it is a good practice to use full paths in scripts.

---

### Post by dcstar on 2008-12-22
> **sn0m said:**
> Hi 
I have written a bash script to record live stream using mplayer.
........
so the cron is runign the script but it is not executing????? Any help to what is actually the problem here?

Thanks in advance
Sokol

The environment cron jobs run in is different from a user shell.

---

### Post by sn0m on 2008-12-22
Thanks a lot guys.
This was my first experience with cron and there was more to it that just getting the syntax right.
I think it is a bit of a handicap that cron cannot run scripts that shell runs.
I'll have a go at setting absolute paths in my script but might need your advice if I get stuck.
Thanks
Sokol

---

### Post by sn0m on 2008-12-25
emmm, i took me a bit of time but I found out what the problem was.
Cron run fantasticly well, however it has got a handicap, as many people rightly pointed out in this thread it has a very limited shell function.
In my script: script that uses mplayer to catch the live stream need to use option" -really-quiet" to run in cron. I found out searching man pages that the verbose function requires GUI to display messages, ie cron can't run it.
So after many frustrating hours, I managed to get it going in cron.
My next thing was to get mp3 tags right but they're not working right now. 
This is my script right now and appreciate if you guys can have a look at it and point out what i'm doing wrong here.
This is the script:

#!/bin/sh
#-------------------------------------------------------------
# A very simple script to capture Rikoshet from Top Albania Radio:
#-------------------------------------------------------------
# Most of the variables:

DATE=`date +%F`  # Save the date as YYYY-MM-DD
YEAR=`date +%Y` # Save just the year as YYYY
FILE=/home/sn0m/Music/rikoshet.$DATE.mp3 # Where to save it
STREAM=http://tar.serverroom.us:9078/
DURATION=30s
MUSIC_DIR=/home/sn0m/Music

# For the id3v2 Tags
AUTHOR="Top Albania Radio"
ALBUM="Rikoshet"
TITLE="Rikoshet - $DATE"


#-------------------------------------------------------------
cd $MUSIC_DIR

# Download the stream and convert it to wave format
#it needs to have -really-quiet option for cron to execute:

/usr/bin/mplayer -really-quiet -vc null -vo null -ao pcm:fast:waveheader:file=stream.wav "http://tar.serverroom.us:9078/" &

sleep $DURATION # Length of the program being recorded as background. 
kill $!         # End the most recently backgrounded job = mplayer

# use soxto adjust volume to the wav file.

sox stream.wav -n stat > stats 2>&1 || exit 1
VOL=$(grep 'Volume' stats | sed 's/^.*[ \t]//')
sox -v $VOL stream.wav rikoshet.wav || exit 1
rm stream.wav
------------------------------------------------------------------------------

# Convert to mp3 and place the appropriate tags:

for i in *.wav; do
 if [ -e "$i" ]; then
   rikoshet=`basename "$i" .wav`
   lame -h -b 192 "$i" "$rikoshet.mp3"
 fi
done

# Tag the resulting captured .mp3
id3v2 -a "$AUTHOR" -A "$ALBUM" \
    -t "$TITLE" -y $YEAR -T 1/1 -g 255 \
    --TCON "Radio" $FILE

# Clean up:

rm rikoshet.wav stats 

#-------------------------------------------------------------end

Thanks in advance
Sokol

---

