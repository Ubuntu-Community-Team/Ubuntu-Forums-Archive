---
title: "The animated PS3 background as wallpaper?"
date: 2009-03-22
forum: Desktop Environments
---

### Post by Locutus_of_Borg on 2009-03-22
[This thing](http://ps3explained.com/wp-content/uploads/2007/11/01-folder-in-photo-menu.jpg) 

On the PS3 it waves and undulates slowly in the background, I'd like to put something like that as my desktop background with xwinwrap and mplayer

Has this been done?

I think I'd just need a video of the animation

---

### Post by Locutus_of_Borg on 2009-03-23
this is what i got so far

[http://www.youtube.com/watch?v=BdlyCQ5zGuw](http://www.youtube.com/watch?v=BdlyCQ5zGuw)


still looking for any better quality video or whatever of the PS3 background

---

### Post by Aaric on 2009-03-23
Quick question what OS are you using. I looked into this before but it didn't work completely for me.
 I found this: 
[http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/](http://tombuntu.com/index.php/2007/09/14/animated-wallpaper-with-compiz-fusion-on-ubuntu/)

---

### Post by Locutus_of_Borg on 2009-03-23
umm i am using Linux



i am already using xwinwrap

i am just looking for the PS3 wallpaper, or a high quality video file of it

---

### Post by Aflack on 2009-03-23
he means what distro most likely such as ubuntu or kubuntu or linux mint... and how did you apply a moving picture as the background?

---

### Post by Locutus_of_Borg on 2009-03-23
oh, the distro is irrelevant to the question entirely

but i am running Gentoo Linux


using xwinwrap and mplayer, you can use any video as your desktop background

---

### Post by Aflack on 2009-03-23
I know it's irrelevant but it would be completely pointless and somewhat dumb to ask if you are running Linux so I assumed he meant distro lol. But I'll have to get this  ... 'xwinrap' ... (probably spelled it wrong there)

---

### Post by Locutus_of_Borg on 2009-03-23
[http://webcvs.freedesktop.org/xapps/xwinwrap/](http://webcvs.freedesktop.org/xapps/xwinwrap/)

download the make file and xwinrap.c to the same directory

open a terminal in that directory and run `make`

you can then run the file xwinwrap that gets created from there or copy it into your PATH

xwinwrap -ni -o 0.9 -fs -s -st -sp -b -nf -- mplayer -wid WID -really-quiet -loop 0 -ao null video.file

will then put the video you specify as your desktop

---

### Post by Aflack on 2009-03-23
That's the 3 year old version. I suggest you go to the new site.[http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap]("http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap")

---

### Post by Locutus_of_Borg on 2009-03-23
oh cool

i'll give it a look, thanks

---

### Post by Aflack on 2009-03-23
np :P and i cant figure it out, but ill keep tryin.

---

