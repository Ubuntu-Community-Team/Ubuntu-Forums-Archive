---
title: "[KDE4.2]Any good application that displays video file information?"
date: 2009-04-09
forum: General Help
---

### Post by kpkeerthi on 2009-04-09
Anything like [this]("http://www.getdeb.net/app/TheMonoSpot") available for KDE4.x. 

I'm not after a GUI application in particular. Any good command-line tool would also work for me. Thanks.

---

### Post by 0cton on 2009-04-09
I don't see why you don't try that particular application itself?
Yes it may require some GNOME libraries and the Mono framework but it works and you keep your Desktop Environement, or am I missing something?

---

### Post by sekinto on 2009-04-09
```
mplayer -identify -frames 0 <file> | grep ID
```

That will give you important video information. You could also easily parse the information and output it in a nicer looking format.

---

### Post by andrew.46 on 2009-04-09
Hi kpkeerthi,

> **kpkeerthi said:**
> Anything like [this]("http://www.getdeb.net/app/TheMonoSpot") available for KDE4.x. 

I'm not after a GUI application in particular. Any good command-line tool would also work for me. Thanks.

You may be interested to read the following thread which discussed this very subject:

[http://ubuntuforums.org/showthread.php?t=1089215](http://ubuntuforums.org/showthread.php?t=1089215)

I believe the best tool for the job that came out of that discussion was Hachoir.

All the best,

Andrew

---

### Post by mb_webguy on 2009-04-09
Well, you do know that applications designed to be used with KDE are still Linux apps, and can be used with any desktop environment, right?

However, personally, I like [MediaInfo]("http://mediainfo.sourceforge.net/en").  From the description of TheMonoSpot, it apparently only works for avi files.  MediaInfo works with *any* kind of video, image, or audio file.  It has a nice GUI, but you can run it from the command-line as well.  

I have a simple script I use with Nautilus Actions to give me a quick "Show media info" option in the Nautilus context menu.  If you'd like to do this as well, just follow these instructions...

First, of course, you need to add the [MediaInfo PPA]("https://launchpad.net/~mediainfo/+archive/ppa") to your Software Sources and install MediaInfo.  Then open a text editor and paste the following into the file:```
#!/bin/bash
gnome-terminal -x sh -c "mediainfo $*; read -n1"

```Save this as "~/bin/mediainfo_nautilus".  Now open the terminal (if you didn't have it open already to edit the script), and type the command:```
chmod +x ~/bin/mediainfo_nautilus
```Now install [Nautilus Actions]("apt://nautilus-actions"), if you haven't already.  Open System->Preferences->Nautilus Actions Configuration.  Click to Add a new entry.  

For the Label, put something like "Show media info".
For the Tooltip, put something like "Display information about multimedia files".
For the Path, put "/usr/bin/gnome-terminal".
For the Parameters, put the following:```
--geometry=120x41 -x sh -c "mediainfo %d/%f;sh"
```You can adjust the values for the geometry option if you like.  Now click OK, and then exit out of Nautilus Actions Configuration.

Now the next time you open a Nautilus window, right-click on any file (though it's really only useful on video, audio, or image files).  You'll see the new "Show media info" option.  Select that, and a terminal window will open showing you all of the media information about that file.  Press any key to close the terminal window.

---

### Post by kpkeerthi on 2009-04-09
Thanks everyone for your help. That helped a lot.

---

