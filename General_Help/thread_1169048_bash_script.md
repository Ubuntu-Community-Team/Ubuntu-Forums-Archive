---
title: "bash script"
date: 2009-05-24
forum: General Help
---

### Post by mysoogal on 2009-05-24
doesn't seem to be working


I'm trying to make this work.

this works, 

```
for i in *.flv; do mencoder -ovc lavc -oac mp3lame -o "$i.avi" "$i"; done
```

but the thing is, i tried to change it into using this


```
#!/bin/bash

# Encoding Script
for i in *.mpeg; do mencoder "$i.avi" -o  "$i" -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame ; done
```

when i run it, error is
```

root@ubuntu:~/Videos# bash encode
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
root@ubuntu:~/Videos# cd /usr/bin/
root@ubuntu:/usr/bin# sudo mv encode /home/yugo/Desktop
root@ubuntu:/usr/bin# 
```

another thing is, can i use something like this so it read all the video containers such as mkv,avi,ogm,mp4,ogg etc

```
for i in *.mpeg,mp4,ogg,ogm,divx,avi,mpg
```

please help !

I'm trying to fix it for hours i just can't figure this thing out


and this is for ffmpeg - h since it seems the first input uses ffmpeg to decode ? 


```
root@ubuntu:/usr/bin# ffmpeg - h
FFmpeg version SVN-r18930, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.33. 0 / 52.33. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on May 24 2009 16:53:29, gcc: 4.3.2
Unable to find a suitable output format for 'pipe:'
root@ubuntu:/usr/bin# 

```

---

### Post by lensman3 on 2009-05-24
Try running your script with the following syntax:

bash -vx ./encode

where encode is your bash script.  The -vx should show the  expanded and executing commands. See if from the expanded scripts you can debug it.

---

### Post by wd5gnr on 2009-05-24
Just a guess. It looks like you must have a path difference in your interactive shell vs your non-interactive shell. A few notes:

1) When doing a script avoid using the ";" so you get error messages that point to the actual line in question. In this case it hardly matters.

2) Run 
which mencoder
To tell you where the binary lives

3) Brute force would be to replace mencoder with /usr/local/bin/mencoder or whatever path step 2 tells you. Not a great general purpose solution though.

4) You could run pwd from the prompt and then run pwd from your shell script and compare the output and track down where your path is getting set in both cases (e.g., .bashrc .profile, etc.)

---

### Post by mysoogal on 2009-05-24
doesnt seem to be working

here is the output


```
root@ubuntu:~/Videos# sudo bash encode
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
root@ubuntu:~/Videos# clear

root@ubuntu:~/Videos# bash -vx /usr/bin/encode
#!user/bin/bash

# Encoding Script
for i in *.mpeg; do mencoder "$i.avi" -o  "$i" -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame ; done
+ for i in '*.mpeg'
+ mencoder diamondufo.mpeg.avi -o diamondufo.mpeg -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame
/usr/bin/encode: line 4: mencoder: command not found
+ for i in '*.mpeg'
+ mencoder germanytri.mpeg.avi -o germanytri.mpeg -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame
/usr/bin/encode: line 4: mencoder: command not found
+ for i in '*.mpeg'
+ mencoder Israel-UFO.mpeg.avi -o Israel-UFO.mpeg -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame
/usr/bin/encode: line 4: mencoder: command not found
+ for i in '*.mpeg'
+ mencoder Lowestoft-UFO.mpeg.avi -o Lowestoft-UFO.mpeg -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame
/usr/bin/encode: line 4: mencoder: command not found
+ for i in '*.mpeg'
+ mencoder phoenix31397.mpeg.avi -o phoenix31397.mpeg -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame
/usr/bin/encode: line 4: mencoder: command not found
+ for i in '*.mpeg'
+ mencoder UFO_Belgium.mpeg.avi -o UFO_Belgium.mpeg -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame
/usr/bin/encode: line 4: mencoder: command not found



root@ubuntu:~/Videos# 

```


also tried with sudo bash 

```
root@ubuntu:~/Videos# sudo bash encode -vx /usr/bin/encode
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
/usr/bin/encode: line 4: mencoder: command not found
root@ubuntu:~/Videos# 


```


i have in my /home/yugo/Videos

2 types of video clips with different container

such as mpeg, and avi

but same video maybe this brings problems ? :o

maybe this line tells me something 

```
+ mencoder Lowestoft-UFO.mpeg.avi -o Lowestoft-UFO.mpeg
```

 its picking up the mpeg and avi but its only set to read mpeg for input ? and for output just avi :o

what is the basic mencoder command with bash ?

---

### Post by mysoogal on 2009-05-24
> **wd5gnr said:**
> Just a guess. It looks like you must have a path difference in your interactive shell vs your non-interactive shell. A few notes:

1) When doing a script avoid using the ";" so you get error messages that point to the actual line in question. In this case it hardly matters.

2) Run 
which mencoder
To tell you where the binary lives

3) Brute force would be to replace mencoder with /usr/local/bin/mencoder or whatever path step 2 tells you. Not a great general purpose solution though.

4) You could run pwd from the prompt and then run pwd from your shell script and compare the output and track down where your path is getting set in both cases (e.g., .bashrc .profile, etc.)

wish i have more experience but you know, im kinda slow with bash. im new
still reading and learning things.

anyway easier way of explaining that :KS

---

### Post by mysoogal on 2009-05-24
hehe never thought i would fix my other automatic transcoding bash script

so here it is

grabs image from avi this can be the whole folder full of avi ;), starts encoding to itu h264 you can also delete the video afterwards.

written originally by FakeOutdoorsman, and I changed it little to my needs and now its time to release it to the ubuntuforums :KS

```
#!/bin/bash
# ffmpeg and mencoder script
# Grab thumb from avi, start encoding to ITU h264 using mencoder, ffmpeg is doing thumb processing

# Bash script for operating system Ubuntu 8.10 
# packages used : FFMPEG, MENCODER ,MPLAYER ENCODING ENGINE
# VIDEO CODEC ITU H264 AUDIO MP3


# Written by FakeOutdoorsman and updated by mysoogal
# Attribution-Noncommercial 3.0 Unported
# http://creativecommons.org/licenses/by-nc/3.0/deed.en
# trackback http://ubuntuforums.org/showthread.php?t=960627

# Location of source videos
sourcelocation="/home/yugo/Desktop/video/"
# Extension of source videos
sourceext="avi"

# grab thumbs hehehe ! yahhoo hope this works!
find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -v 0 -y -i {} -vframes 1 -ss 90 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 {}.jpg \;
# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}*.ogm" ] && [ -e "${sourcelocation}*.jpg" ]; then
	# Delete videos	
	rm ${sourcelocation}*.ogm
	# Sleep for 10 seconds before shutting down
	sleep 10
	# Shutdown computer
	# sudo shutdown -h now
else
	echo "Encoding FAILED"
fi


# Convert all video clips to ITU H264 OGM video container
find ${sourcelocation} -iname "*${sourceext}" -exec mencoder {} -o {}.ogm -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=300:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto -oac mp3lame \;



exit
```



the future plan is to have this do cron job every 15 minutes or so. depending on the video size etc. encoding could take 55 minutes for 700 mb.

---

### Post by andrew.46 on 2009-05-25
Hi mysoogal,

I see you have tried a few different approaches but can I make a few points about the following:

> **mysoogal said:**
> 

```

for i in *.mpeg; do 
mencoder "$i.avi" -o  "$i" -af volume=10 -aspect 16:9 -of avi -noodml \
-ovc x264 -x264encopts bitrate=500:level_idc=41:bframes=3:frameref=2: nopsnr: nossim: pass=1: threads=auto \
-oac mp3lame ; 
done
```


[LIST=1]
[*]A basic problem is that the avi format is not the best for h264 video and especially with B-frames. A better choice would be mp4 or matroska.
[*]Your video chain has some spaces after the ':' which might account for the error messages.
[*] The 2 options '-of avi' 'pass=1' are not really necessary.
[/LIST]

I guess a final point might be that FFmpeg tends to do a much better job with this sort of transcoding particularly if you are happy to use the new presets.

All the best,

Andrew

---

### Post by benson444 on 2009-05-25
> **mysoogal said:**
> 

another thing is, can i use something like this so it read all the video containers such as mkv,avi,ogm,mp4,ogg etc

```
for i in *.mpeg,mp4,ogg,ogm,divx,avi,mpg
```


I think you can do that using curly brackets around the extensions

```
for i in *.{mpeg,mp4,ogg,ogm,divx,avi,mpg}
```

---

