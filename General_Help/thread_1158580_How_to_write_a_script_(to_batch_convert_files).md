---
title: "How to write a script (to batch convert files)?"
date: 2009-05-13
forum: General Help
---

### Post by Nixie Pixel on 2009-05-13
Hi, I'm trying to put together a script to batch convert .MOV files into .asf (Windows Media) files using ffmpeg.

I found the following to use as a guide:
```
for f in *.flv; do ffmpeg -i $f $f.avi; done
```

But I want it to be a bit more complex, so I need a little help understanding the syntax...

I want to batch convert with options similar to this:  ffmpeg -i movfilex.MOV -vcodec wmv2 -sameq -acodec wmav2 -f asf movefilex.asf

So if I write: 
```
for f in *.MOV; do ffmpeg -i $f -vcodec wmv2 -sameq -acodec wmav2 -f asf $f.asf; done
```
Should it work?  Does the first $f imply f.MOV?  If so, wouldn't the output file be named something like movfilex.MOV.asf?

Thanks!

---

### Post by aeiah on 2009-05-13
yes it will. why didnt you just try it though? :p

you'll have to either include a function that grabs the base filename and use that instead of $f or batch rename the files after conversion, removing the .MOV section of each filename

---

### Post by mc4man on 2009-05-13
A basic batch convert command keeping the same filename for ffmpeg would be 
Ex for aac2wav

for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.wav"; done

so maybe (or adjust as needed

```
for f in *.MOV; do ffmpeg -i "$f" -vcodec wmv2 -sameq -acodec wmav2  "${f%.MOV}.asf"; done
```


Edit
Don't convert video much so not sure about whether you should be using .asf as an ext. (maybe .mp4

---

### Post by andrew.46 on 2009-05-13
Hi Nixie Pixel,

> **Nixie Pixel said:**
>  wouldn't the output file be named something like movfilex.MOV.asf?

Which is a little untidy :-). You could try something like:

```
for f in *.MOV; do ffmpeg -i $f -vcodec wmv2 -sameq -acodec wmav2 -f asf **[COLOR="Red"]$(echo $f | sed 's/\.[^.]*$//').asf[/COLOR]**; done
```

which should convert a file called 'test.MOV' to 'test.asf', this is a little tidier? How cool is FFmpeg combined with a 'for' loop and sprinkled with a little sed magic!!

All the best,

Andrew

---

### Post by petrus4 on 2009-05-13
> **Nixie Pixel said:**
> 
So if I write: 
```
for f in *.MOV; do ffmpeg -i $f -vcodec wmv2 -sameq -acodec wmav2 -f asf $f.asf; done
```
Should it work?  Does the first $f imply f.MOV?  If so, wouldn't the output file be named something like movfilex.MOV.asf?

Yes, that $f does imply .MOV.

I'd go...

```

#!/bin/sh -x

ffargs='-i $f -vcodec wmv2 -sameq -acodec wmav2 -f asf ${f}.asf'

for f in *.MOV 
do 
ffmpeg $ffargs

fixedfilename= `echo ${f}.asf | sed -e s'@.mov@@'g`
mv ${f}.asf ${fixedfilename}

done

```

I generally do just about everything in a file, evenly spaced out across multiple lines, rather than trying to cram everything into one line and hold multiple abstractions (in some cases) in my head at once.  It makes things much simpler, and means that even when I screw up, (which is often) debugging is actually a tolerable experience.

Don't be afraid to space things out, and if you're using shell variables in amongst other stuff, I generally try and remember to brace them as well, as it increases readability.  That can cause issues though, particularly with sed, so you can't do it all the time.

The '-x' switch to bash enables output of everything it does as well.  Bash's debugging still isn't all that great, but it's a lot better than nothing at all.  With -x turned on tho, you can then execute the script with:-

```
./script.sh 2>&1 | tee script.log
```

This gives you the equivalent of a flight recorder.  If you get syntax errors or whatever else, reading the log (or even just what scrolls on the screen when you execute the script) will hopefully give you an idea of where you've gone wrong.

---

### Post by Nixie Pixel on 2009-05-13
Hi, thanks for the replies!  I guess I was nervous to try it because I don't like seeing nasty error messages when I mess up!  ;)

I will definitely have to try that more complicated version to try and convert them with clean filenames.  Thank you!

And yes, I absolutely love ffmpeg, especially when I have to convert a ton of video footage prior to editing.  I was doing each one manually before, so this script will be amazing for me!

I think I will make my next linux quickie video about the joys of multimedia conversion with ffmpeg.

Thanks again!

~Nix

---

### Post by Nixie Pixel on 2009-05-17
Thanks for all the help!  I had one last question - do these scripts work for all Linux distributions?  If not, what are the limitations?

Thanks!

---

### Post by andrew.46 on 2009-05-18
Hi Nixie Pixel,

> **Nixie Pixel said:**
> Thanks for all the help!  I had one last question - do these scripts work for all Linux distributions?  If not, what are the limitations?

These scripts and their variations should definitely work on other distros that run bash. Can anyone comment on other shells?

BTW love your site :-).

Andrew

---

### Post by mb_webguy on 2009-05-18
Take note of the shebang -- the line at the top of the script that starts with "#!".  This tells the system what shell to use to interpret the script.  A script that starts with "#! /bin/sh" will be interpreted using the Bourne shell (or possibly a faster Bourne-compatible shell like dash).  As long as that shell (or a compatible one linked as the required shell) is installed on the system, the script will work just fine.

Scripts written for sh (the Bourne shell) will work in any Bourne-compatible shell such as bash and dash, but the reverse is not necessarily true.  That's partly why you'll see so many scripts written for sh.  Practically every system running a Unix-like OS will run a Bourne shell script, and those that won't just need to have the shell installed first.

---

### Post by mysoogal on 2009-05-27
this probably makes things much easier for you.

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
sourcelocation="/home/username/Videos"
# Extension of source videos
sourceext="avi"

# grab thumbs hehehe ! yahhoo hope this works!
find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -v 0 -y -i {} -vframes 1 -ss 90 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 {}.jpg \;
# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}/*.avi" ] && [ -e "${sourcelocation}/*.jpg" ]; then
	# Delete videos	
	rm ${sourcelocation}/*.avi
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
replace your username with your real username

> **sourcelocation="/home/your username/Videos"**

to change what type of input just rename this to mov, etc

> sourceext="avi" to sourceext="mov"


put this bash script into /usr/bin/

simply go into cd /home/Username/Videos

and sudo scriptname 

will encode every video in this folder and grab thumbs to ;)

if something doesnt work tell me about it, its working fine for me.

---

### Post by domzz on 2010-05-19
> **mysoogal said:**
> this probably makes things much easier for you.

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
sourcelocation="/home/username/Videos"
# Extension of source videos
sourceext="avi"

# grab thumbs hehehe ! yahhoo hope this works!
find ${sourcelocation} -iname "*${sourceext}" -exec ffmpeg -v 0 -y -i {} -vframes 1 -ss 90 -vcodec mjpeg -f rawvideo -s 286x160 -aspect 16:9 {}.jpg \;
# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}/*.avi" ] && [ -e "${sourcelocation}/*.jpg" ]; then
	# Delete videos	
	rm ${sourcelocation}/*.avi
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
replace your username with your real username



to change what type of input just rename this to mov, etc




put this bash script into /usr/bin/

simply go into cd /home/Username/Videos

and sudo scriptname 

will encode every video in this folder and grab thumbs to ;)

if something doesnt work tell me about it, its working fine for me.

How can I change this so it encodes the video in every sub directory instead of main directory and moves the files to a new directory deleting the old subdirectory.

---

