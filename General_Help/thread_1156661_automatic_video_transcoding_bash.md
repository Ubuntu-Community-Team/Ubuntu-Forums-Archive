---
title: "automatic video transcoding bash ?"
date: 2009-05-11
forum: General Help
---

### Post by mysoogal on 2009-05-11
hi, I'm looking for a automatic video transcoding bash script

which does exactly what thread title suggests

take this as for example, if you have a script this does something like this.

I'm running a directory php script which lists avi,flv,mpeg etc from here when I click on any video it will open the vlc web plguin this script this has uploading support, lets say i want to upload to /var/www/uploads/ i want this bash script to be a demon based you know system service based and go in loops searching for new files, so when it detects there is video in this directory it will fire this bash script, so encoding process starts.

when encoding process finishes, it will move these new encoded file to lets say /var/www/vdata/


thats about it, its kinda a dirty video sharing encoding site I'm trying to achieve .:KS.


please let me know, where i can find some automatic mencoder or ffmpeg, etc bash scripts which let me do these things.

thanks

---

### Post by FakeOutdoorsman on 2009-05-12
This might help you out:
[Automating video conversion for a beginner](http://ubuntuforums.org/showthread.php?t=960627)

---

### Post by mysoogal on 2009-05-14
> #!/bin/bash
# ffmpeg and mencoder script
# grab thumb from avi, start encoding to itu h264 using mencoder, ffmpeg is doing thumb processing

# bash script for operating system ubuntu 8.10
# packages used : Ffmpeg, mencoder ,mplayer encoding engine
# video codec itu h264 audio mp3


# written by fakeoutdoorsman and updated by mysoogal
# attribution-noncommercial 3.0 unported
# [http://creativecommons.org/licenses/by-nc/3.0/deed.en](http://creativecommons.org/licenses/by-nc/3.0/deed.en)
# trackback [http://ubuntuforums.org/showthread.php?t=960627](http://ubuntuforums.org/showthread.php?t=960627)

# location of source videos
sourcelocation="/var/www/uploads/"
# extension of source videos
sourceext="mpeg"


# grab thumbs hehehe ! Yahhoo hope this works!
Find ${sourcelocation} -iname "*${sourceext}" -exec /usr/local/bin/ffmpeg -v 0 -y -i {} -vframes 1 -ss 200 -vcodec mjpeg -f rawvideo -s 200x130 -aspect 16:9 {}.jpg \;
# check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}*.avi" ] && [ -e "${sourcelocation}/*.jpg" ]; then
	# delete videos	
	rm ${sourcelocation}/*.avi
	# sleep for 10 seconds before shutting down
	sleep 10
	# shutdown computer
	# sudo shutdown -h now
else
	echo "encoding failed"
fi


# convert all video clips to itu h264 ogm video container
find ${sourcelocation} -iname "*${sourceext}" -exec mencoder {} -o {}.ogm -af volume=10 -aspect 16:9 -of avi -noodml -ovc x264 -x264encopts bitrate=300:level_idc=41:bframes=3:frameref=2: Nopsnr: Nossim: Pass=1: Threads=auto -oac mp3lame \;


exit


..........
..........
..........

---

### Post by FakeOutdoorsman on 2009-05-15
> **mysoogal said:**
> thanks dude, your the best! 

now time to learn this thing

few more questions if you don't mind

can you please check if this is right, also it seem it will reboot. how to safely remove this feature with # ?
Either delete that line, or comment it out with #:
```
# sudo shutdown -h now
```


> 
i don't get this thing

```
rm ${sourcelocation}/*.dv
```

what is it, a folder ? called dv ?

is this for video input
The user who I made this example for wanted his input .dv files to be deleted after conversion.  This command deletes all .dv files after conversion, but it isn't the best way to do this as I mentioned in the thread I linked to earlier.

> can i use something like this
```

# Extension of source videos
sourceext="avi,mpg,mpeg,mov,3gp,rmvb,rm,ogm,mp4,m4v"
```
I'm definitely not much of a script writer, as you can see by my simple example.  I think the script will look for an extension that would look something like this:
```
inputfile.avi,mpg,mpeg,mov,3gp,rmvb,rm,ogm,mp4,m4v
```
> was wondering can this thing communicate with mysql database ? or php

maybe have a index.php to show all the encoded videos.
I don't know how to do that.  You may want to ask in the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) section of this forum.

---

### Post by mysoogal on 2009-05-15
thanks i'll be doing that !

---

### Post by mysoogal on 2009-05-25
> inputfile.avi,mpg,mpeg,mov,3gp,rmvb,rm,ogm,mp4,m4v

this works instead > sourceext="$input"

should read any input :D

---

### Post by mysoogal on 2009-05-29
**[SIZE="6"][COLOR="DarkOrange"]YES its [COLOR="Plum"]complete[/COLOR] ! this is it ![/COLOR][/SIZE]**

fully working **[COLOR="RoyalBlue"]automatic[/COLOR]** **transcoding **bash script, fully working with 

**> sudo Install Gnome-schedule **

if your using this script, you can use this Gnome-schedule, and set the bash script to run every hour ? or every single day at certain time !;)

more information about this Gnome-schedule
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

-----------------------------------------------------------------

with this you can have a very easy video sharing script powered by Gnome-schedule ! and web server and a php directory script which plays video such as [http://greg-j.com/phpdl/](http://greg-j.com/phpdl/) this script enables you to stream flv 

you get the idea ! inside the bash script you can change the mencoder or ffmpeg to encode to flash flv1 instead.


thanks everybody who helped me. :KS thanks very much

---

