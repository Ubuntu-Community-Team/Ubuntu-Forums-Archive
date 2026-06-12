---
title: "Mplayer Resize Issues"
date: 2006-01-08
forum: General Help
---

### Post by GreenAdder on 2006-01-08
I recently installed Mplayer (I used Synaptic) and edited the config file as instructed in the Ubuntu Wiki page ([https://wiki.ubuntu.com/MplayerInstallHowto)](https://wiki.ubuntu.com/MplayerInstallHowto)).  Everything works fine and the audio sync issues I had with Ubuntu 5.04 seem to be gone, but now I have the problem where I can't resize video.

When I try to resize the video window or select "Fullscreen," I just get a black border with the original-sized video in the middle.  This also happens if I switch aspect ratios.  For instance, going from 4x3 to 16x9 just presents a black (or sometimes blue) 16x9 window with a 4x3 picture in the middle.

This happens regardless of format, framerate, bitrate, etc.  ASF, WMV, MPEG, AVI, Quicktime, DivX, and even OGM files all have this issue.  Can anyone suggest a fix?  

While not likely, might it have something to do with me using the general i386 version of Mplayer and not the Athlon-specific one?

Thanks.

---

### Post by nhisyam on 2006-01-08
try this

sudo gedit /etc/mplayer/mplayer.conf

change vo=x11 to vo=xv

hope this helps.

---

### Post by soulestream on 2006-01-08
search the forum

google

go into preferences -> video -> xv (probably)

restart mplayer


soule

---

### Post by GreenAdder on 2006-01-08
I actually did search the forum.  I went through about 100 threads without an answer, and that's why I posted.

But thanks, guys.  Switching from x11 to xv did the trick.

---

### Post by lleberg on 2006-01-09
I have the same problem, but I get an error when switching to xv!
"Error opening/initializing the selected video_out (-vo) device."

Why is this?

---

### Post by duminas on 2006-01-09
This is to lleberg:

Run this on the terminal (Applications > Accessories > Terminal):
```
echo "zoom=yes" >> ~/.mplayer/config
```In case you're curious, that just appends "zoom=yes" (without quotes, of course) to the .mplayer/config file in your home directory. Should fix the issue--it fixed mine without using the vo=xv bit (which also spat that error you're mentioning).

[size=1](**Really** bugs me that this got screwed up on 5.10, and it's part of the reason I'm still using 5.04. Oh well.)[/size]

---

### Post by lleberg on 2006-01-09
[QUOTE=duminas]This is to lleberg:

Run this on the terminal (Applications > Accessories > Terminal):
```
echo "zoom=yes" >> ~/.mplayer/config
```In case you're curious, that just appends "zoom=yes" (without quotes, of course) to the .mplayer/config file in your home directory. Should fix the issue--it fixed mine without using the vo=xv bit (which also spat that error you're mentioning).

[size=1](**Really** bugs me that this got screwed up on 5.10, and it's part of the reason I'm still using 5.04. Oh well.)[/size][/QUOTE]

That's a really good sollution!
And of course, it works!
Thanks. :)

---

### Post by patrick295767 on 2006-01-14
Thank you very much 
echo "zoom=yes" >> ~/.mplayer/config

works very well !!

thaaannk you !

---

