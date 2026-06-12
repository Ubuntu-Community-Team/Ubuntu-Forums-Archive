---
title: "Convert videofiles?!"
date: 2006-01-15
forum: General Help
---

### Post by KhanArash on 2006-01-15
How can I convert Video files like .avi, .wma, and other video files to another format which can run in a dvd-player?
And how can I burn a dvd?!

THnkx Arash

---

### Post by KhanArash on 2006-01-15
CAn anyone please help?:confused: :KS :confused:

---

### Post by putte30 on 2006-01-15
Check out avidemux and k3b,

---

### Post by niviche on 2006-01-15
The service menu at [http://www.kde-apps.org/content/show.php?content=30455](http://www.kde-apps.org/content/show.php?content=30455) should help you. And if it doesn't, the mencoder ffmpeg apps it recommends might do.

---

### Post by KhanArash on 2006-01-15
putte30
Check out avidemux and k3b

I found k3b, but how do i find avidemux?

---

### Post by KhanArash on 2006-01-15
[QUOTE=niviche]The service menu at [http://www.kde-apps.org/content/show.php?content=30455](http://www.kde-apps.org/content/show.php?content=30455) should help you. And if it doesn't, the mencoder ffmpeg apps it recommends might do.[/QUOTE]

```
To install, just copy and paste the source code into the file /usr/share/apps/konqueror/servicemenus/konqkonv.desktop (or /opt/kde3/share/apps/konqueror/servicemenus/ under SUSE) The video conversion options will then appear under the 'Actions' menu when you right-click a video file.
```

I open it and with this code: sudo gedit /usr/share/apps/konqueror/servicemenus/konqkonv.desktop

but i cant save it!! do you know why?!and do you know what I need to install or do to get it work?

---

### Post by niviche on 2006-01-15
First, are you using Gnome or KDE? This service menu is for KDE.

Then, what error do you get when you want to save this menu?

Finally, do you have mencoder installed?

---

### Post by KhanArash on 2006-01-15
I use Gnome!

---

### Post by KhanArash on 2006-01-15
Do you know about a program in UBuntu which can convert those video files?

---

### Post by rattking on 2006-01-15
look into 
tovid
[http://tovid.berlios.de/](http://tovid.berlios.de/)
it does this and menus.. 
i then use k3b to burn the resulting video_ts

---

### Post by Kjell on 2006-01-15
Hej,

I gues it is ffmpeg that can convert various media formats, as it is command line and perhaps little difficult to get used to - you can use other programs that uses ffmpeg, check any suitable GUI at 

[http://ffmpeg.sourceforge.net/projects.php](http://ffmpeg.sourceforge.net/projects.php)

right now In I'm just using dvd::rip to convert video formats annd to ripp dvd's
for simple video cutting I use avidemux for my mpeg-ts (streaming mpeg) files


//Kjell

---

### Post by mmackinl on 2006-01-23
Trying **avidemux** to convert avi's to SVCD but I always get the message :* Save(A+V) will generate bad AVI Save audio will work* ....... and can do nothing with the audio. Can anyone tell me what I'm missing?

---

### Post by jtpratt on 2006-03-14
I struggled with the same questions.

Read my Ubuntu guide to converting video with ffmpeg here:
[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)

---

