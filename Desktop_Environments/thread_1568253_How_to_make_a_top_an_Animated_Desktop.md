---
title: "How to make a top an Animated Desktop"
date: 2010-09-04
forum: Desktop Environments
---

### Post by donut123 on 2010-09-04
[SIZE=4]Hello...I would like to know how to make an Animated Desktop [/SIZE].[SIZE=4] I have seen 2 videos on you tube..but were not clear on how it is exactly done.    I would  like to  know the correct way.[/SIZE]
Thank you :)

---

### Post by nick_goodfate on 2010-09-05
Animated Desktop? You have to be a little more specific... You mean something like [[COLOR="Orange"]this[/COLOR]]("http://www.omgubuntu.co.uk/2010/08/dreamscene-for-ubuntu-ta-very-much/")?

---

### Post by donut123 on 2010-09-05
> **nick_goodfate said:**
> Animated Desktop? You have to be a little more specific... You mean something like [[COLOR=Orange]this[/COLOR]]("http://www.omgubuntu.co.uk/2010/08/dreamscene-for-ubuntu-ta-very-much/")?Yes something like that...but I think it can be done with any gif...or video also.
OK I installed that app..however I cannot find it in my apps. I am going to hold off for a while. 
Untill I can find it. 
shantz-xwinwrap is noweher to be found in my apps.
I1ll be back
thank you

---

### Post by nick_goodfate on 2010-09-05
[http://www.youtube.com/watch?v=WIbJ5S3PUJc](http://www.youtube.com/watch?v=WIbJ5S3PUJc)

EDIT: I started to follow the instructions of the video and found that A-desk script costs 1$. Sad...

---

### Post by donut123 on 2010-09-05
> **nick_goodfate said:**
> [http://www.youtube.com/watch?v=WIbJ5S3PUJc](http://www.youtube.com/watch?v=WIbJ5S3PUJc)

EDIT: I started to follow the instructions of the video and found that A-desk script costs 1$. Sad...
I see it costs money..I dont have a credit card. 
I guees ILl find out some day how to do it. 
Thank you

---

### Post by mcduck on 2010-09-06
> **donut123 said:**
> Yes something like that...but I think it can be done with any gif...or video also.
OK I installed that app..however I cannot find it in my apps. I am going to hold off for a while. 
Untill I can find it. 
shantz-xwinwrap is noweher to be found in my apps.
I1ll be back
thank you

xwinwrap is a command-line applicaton, it's not going to appear in your menus.

On the other hand if you don't want 3D or video as your wallpaper, Gnome has built-in support for wallpaper slideshows. You just need to create an XML file that tells it what images to use, and how long to display each image & fade to next one. I believe there's also some GUI tool for creating this kind of animated wallpapers.

---

### Post by nick_goodfate on 2010-09-06
ok i tried the guide from my first post in this thread and it works, but not perfectly. Every time the video finishes before it starts again i see black screen for half a second... Also my cpu temp rises to 65 Celsius.

---

### Post by donut123 on 2010-09-07
> **nick_goodfate said:**
> ok i tried the guide from my first post in this thread and it works, but not perfectly. Every time the video finishes before it starts again i see black screen for half a second... Also my cpu temp rises to 65 Celsius.

Ok here is the answer.





First install dependencies

sudo apt-get install zenity mplayer

sudo apt-get install xorg-dev build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs -y

Untar Install the xwinwrap.deb for your system 32 or 64 Bit

Open  your "home folder" click "view" click "show hidden files" click  ".gnome2" click "nautilus scripts"  Place "Ultimate Animated" in  "nautilus scripts folder" and close log out and in, right click on  desktop scripts> "Ultimate Animated" (at the bottom of the scripts  menu!) [IMG]http://www.ultimateeditionoz.com/forum/images/smilies/grin.png[/IMG]You can get more movies here
See the attached files.

[http://www.archive.org/details/electricsheep-packs-244](http://www.archive.org/details/electricsheep-packs-244)
[IMG]http://i245.photobucket.com/albums/gg60/Donut_123/donutwashere.gif[/IMG]Have fun !
[SOLVED]

---

### Post by MKSLLR on 2010-09-18
The directions given above worked out nicely. However, the video freezes when I use the Static Application Switcher. It's only a minor annoyance but is there a way to stop it from freezing?  (I'm a 10.04 user, btw)

---

### Post by MKSLLR on 2010-09-20
Oh yeah, and how to make it run on startup?

If anyone bothers, thanks in advance

---

### Post by donut123 on 2010-09-20
> **MKSLLR said:**
> Oh yeah, and how to make it run on startup?

If anyone bothers, thanks in advance
Im sorry buddy that you are not happy. 
I cannot please everyone..I apologize for 
offending you.
Have a nice and pleasant journey.
And by the way this was SOLVED  
and perhaps ones will bother.
[[IMG]http://www.ultimateeditionoz.com/forum/images/smilies/splat.gif[/IMG]]("http://www.ultimateeditionoz.com/forum/posting.php?mode=quote&f=148&p=6806#")

---

### Post by nick_goodfate on 2010-09-21
> **donut123 said:**
> Im sorry buddy that you are not happy. 
I cannot please everyone..I apologize for 
offending you.
Have a nice and pleasant journey.
And by the way this was SOLVED  
and perhaps ones will bother.


No one asked you to please everyone... He asked something relevant to the subject of this thread, in a [SIZE="7"]SUPPORT[/SIZE] forum. If you can't help him you have the option to not answer... 

MKSLLR, as this thread is marked as solved (if op don't want to mark it as unsolved again) you should probably start a new thread, with a link to this one, in order to find some help.

---

### Post by LinuxPhreak on 2010-09-22
> **MKSLLR said:**
> Oh yeah, and how to make it run on startup?

You can make it start at startup by going to System > Preferences > Startup Applications

From here a window will appear. Click the Add Button. Then give it any old name. Then add the command you use to start it up. Each user will have to do this. If you want it for each user then you will have to modify gconf.

---

