---
title: "Problems Uploading via Flash"
date: 2009-05-26
forum: General Help
---

### Post by jdorenbush on 2009-05-26
I am having problems uploading files (mainly photos) via Flash through websites like Flickr and Myspace.

This wasn't a problem in 8.10, but after upgrading it has been a problem. The actual Flash itself seems to work, but when I actually try and proceed with the upload process it doesn't do much.

I tested to make sure Flash was installed at:
[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

Came back OK. Except for Shockwave -- I don't believe Shockwave is the problem.

Thoughts?

---

### Post by jdorenbush on 2009-05-28
Still trying to get to the bottom of this issue. Anyone?

---

### Post by jdorenbush on 2009-10-21
Either something was updated with Firefox, Flash or Ubuntu in general, but this appears to magically no longer be a problem. 

Not sure if anyone else was having a problem with this, but it appears to be fixed. Don't know how it was fixed, I sort of wish I knew, but I am happy enough that it is just fixed.

---

### Post by Eenvoud on 2009-11-04
Hm I have the same problem with uploading an audio file on myspace...the flash box appears, but the uploading never gets going

Was it the upgrade to Karmic Koala that fixed it? Because I'm still using Jaunty...I always tend to wait a bit and let others debug before I do an upgrade ;)

---

### Post by jdorenbush on 2009-11-04
These are the steps I took..try it and let us know if it works.

1. Remove the "flashplugin" via Synaptic Package Manager

2. Download: [Flash Player 10 for 64-bit Linux]("http://labs.adobe.com/downloads/flashplayer10.html")

3. Extract downloaded file (libflashplayer.so) into /usr/lib/mozilla/plugins/ by hitting Alt+F2, and typing "gksu nautilus". Then hit enter and navigate to the /plugins/ directory.

4. Reboot (Not sure if this is necessary, but I tried launching Firefox after I installed new Flash plugin and I was having problems. Reboot seemed to have solved that problem.)

---

### Post by Eenvoud on 2009-11-05
Thx for the suggestion! I did a manual reinstallation using the 32-bit version but still get the same problem...something I noticed: manually, the plugin is indeed called libflashplayer.so. But when I install it via synaptic (sudo apt-get install flashplugin-installer), it's called flashplugin-alternative.so. Don't know if that's of any importance, just throwing it out there.

Btw is it possible to unmark this as solved so more people might read this and help? Thx!

---

### Post by Mighty_Joe on 2009-11-05
> **Eenvoud said:**
>  Don't know if that's of any importance, just throwing it out there.


It's somewhat important.  Ubuntu uses a system of "alternatives" for programs like Java and Flash that can have multiple versions.  The files you see in the plugin directory are actually symlinks to the real program somewhere else. 
Obviously, if you install Flash manually, you are bypassing the "alternatives" system, so the symlink will be named differently.
I've had problems uploading files to MediaFire in 9.04, as [have others]("http://ubuntuforums.org/showthread.php?t=1288089&highlight=mediafire").  I'm not aware of a fix or workaround other than using Windows.

---

### Post by jdorenbush on 2009-11-05
> **Eenvoud said:**
> Btw is it possible to unmark this as solved so more people might read this and help? Thx!


I marked it as unsolved for you. I don't have any other suggestions right now. Hopefully someone else can help you out. Good luck!

---

### Post by Eenvoud on 2009-11-06
thx!

> **Mighty_Joe said:**
> It's somewhat important.  Ubuntu uses a system of "alternatives" for programs like Java and Flash that can have multiple versions.  The files you see in the plugin directory are actually symlinks to the real program somewhere else. 
Obviously, if you install Flash manually, you are bypassing the "alternatives" system, so the symlink will be named differently.
I've had problems uploading files to MediaFire in 9.04, as [have others]("http://ubuntuforums.org/showthread.php?t=1288089&highlight=mediafire").  I'm not aware of a fix or workaround other than using Windows.
lol that's what I wanted to do in the end but then my Vista was completely screwed up for some reason...can you believe it? Only really used it for skype thus far - yeah my webcam doesn't work properly in Ubuntu, it's always something isn't it...another problem is getting my wireless to work, gonna try again now

---

