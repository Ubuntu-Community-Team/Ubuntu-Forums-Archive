---
title: "anyone know a good program for dvd's?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by starwarsfan982 on 2006-09-14
Hi. I'm looking for a replacement for ffmpeg. I have multiple .vob files that  I need to convert to one avi file so the program will have to do that. GUI or Command Line is fine. Thank you.

Dylan

---

### Post by ciscosurfer on 2006-09-14
I'm checking on some possible replacements now...i'll get back to you ;-)

---

### Post by Shay Stephens on 2006-09-14
I convert recorded tv shows to ogg in a two step process.  The first step is getting the vobs into one file, then converting that to a 320x240 ogg file.  I am using this currently:

```
mencoder -dvd-device path_to_dvd dvd://1 -ovc copy -oac pcm -o ripped.avi
```

In my case, the "path_to_dvd" is "/media/cdrom0". Which in turn, turns the multiple vob files into one long video file called "ripped.avi".  dvd://1 tells it to grab the first video.  You might have to change the number based on what video on the dvd you want to work with.

Then I downsample it and convert to ogg theora video format with this:

```
ffmpeg2theora -v1 -a1 -c1 -x320 -y240 ripped.avi
```
v1 is low quality video, a1 is low quality audio, and c1 is mono.

Which creates the file ripped.ogg

---

### Post by ciscosurfer on 2006-09-14
Enable your [COLOR=Sienna]universe[/COLOR] repo and then install [COLOR=Red]pitivi

[COLOR=Black]or[/COLOR]

[COLOR=DimGray]Enable your [COLOR=Sienna]multiverse[/COLOR] repo and then install [COLOR=Red]qdvdauthor[/COLOR][/COLOR]
[/COLOR]

---

