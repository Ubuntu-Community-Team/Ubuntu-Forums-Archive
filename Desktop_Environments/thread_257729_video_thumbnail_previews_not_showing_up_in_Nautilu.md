---
title: "video thumbnail previews not showing up in Nautilus"
date: 2006-09-14
forum: Desktop Environments
---

### Post by yeehawjared on 2006-09-14
My videos aren't showing up.  I have the codecs - they play fine in Mplayer.  They Do NOT play in Movie Player though... which is weird

All other types of thumbnails show up properly - pictures, text files, etc.

Anyone have this problem?  What packages should I install/reinstall?  I have xine/gstreamer.

see attached screenshot... thanks guys. :)

---

### Post by yeehawjared on 2006-09-14
one more thing, beep-media-player doesn't finish installing in automatix when i try to install non-free codecs.

---

### Post by Anduu on 2006-09-15
How about other video formats...do they show thimbnails.I notice all those in your screenshot are xvid.

---

### Post by yeehawjared on 2006-09-15
yeah, all of those are xvid, but avi,wmv,mpg,etc. don't show up either.

I've followed a few more "how to get non-free codecs installed guides" but still no preview.

What's weird is that this is the third time I've installed Ubuntu.  The other two installs worked perfectly - I'm using the same MD5 hash verified ISO.  I have XGL/Compiz working perfectly, nothing else seems broken.  

I always use automatix to get the non-free codecs with movie players.  Do you think it has something to do with beep-media-player not being in the repositories?

---

### Post by Anduu on 2006-09-15
Ok lets try this...

Open the configuration Editor and go to desktop>gnome>thumbnailers.

The entry for the various formats should look something like this:
```
command /usr/bin/gnome-video-thumbnailer -s %s %u %o
```

Make sure the enable box is checked.

You may need to log out and back in for any changes to take effect.

---

### Post by yeehawjared on 2006-09-16
yeah all of those are enabled with the same string.


figured something out just now.  looking in another torrent folder I see that all the movies have thumbnails.  It's just certain folder that recursively don't generate previews.  The permissions (group, owner, etc) are the same for all though - it's my external hard drive.

My torrent folder works fine, all video formats are great.  Yet, on the same hard drive, in a different folder NONE of the movies generate previews.  weird huh?  They all contain the same general formats - avi/xvid/mpg

guess it's a permissions thing.  I can live without permissions for a folder

---

### Post by Anduu on 2006-09-16
OKDk...one last thing to do/try.

From the panel menu go to System>Preferences>File Management and select the preview tab.Adjusting the settings in here should straighten that out.They are pretty self explanitory.

Be aware however that not all movies can generate a thumbnail...for instance there is one avi on my hard drive that doesn't have a thumbnail while all my others do...go figure :p

---

### Post by yeehawjared on 2006-09-16
System>Preferences>File Management   don't see it.  

in gconf-editor?  sorry man, still learning.  btw, it's so nice you helping me out... this community is rock solid.  I'm trying to return the favor as much as I can.

---

### Post by ciscosurfer on 2006-09-16
@yeehawjared,

You can delete your icon cache and start clean...see if that helps.

Open Nautilus, go to View > Show hidden files 
Click the directory called .thumbnails
You can then open 'fail', 'normal', or 'large' (if you have it) and delete all files within.  You can also just delete the directories (they get replaced when you open a directory with pictures, videos, etc.)

---

### Post by ciscosurfer on 2006-09-16
You can also mess around with the Preferences settings within Nautilus (your file manager).  Go to Edit > Preferences > Preview.

---

### Post by yeehawjared on 2006-09-16
sorry, don't see any .thumbnail folders

not even when i ls -la

see attachment

---

### Post by Anduu on 2006-09-16
> **yeehawjared said:**
> System>Preferences>File Management   don't see it.  

in gconf-editor?  sorry man, still learning.  btw, it's so nice you helping me out... this community is rock solid.  I'm trying to return the favor as much as I can.

Heh thas ok...it is in the gnome panel at the top of your screen..Applications,Places...System... ;)

---

### Post by ciscosurfer on 2006-09-16
Ok.  So the folder (Linux calls them directories) that has all your videos in it, in the left pane called Places, click your name "jared" this will take you to your /home/jared directory.  Now, follow my instructions from my last post (you can also view hidden files by using Control-H)...

---

### Post by yeehawjared on 2006-09-16
i figured out the cause of the problem:

Certain folders won't recursively thumbnail videos.  When I move that folder into a different folder all thumbnails load just fine.  For example:

ExternalHd\greysanatomy\file.avi  - doesn't preview  I move the directory to:
ExternalHd\torrents\greysanatomy\file.avi - DOES work.  Same folder, same file, just in a different location.

I even chmod -R 777 my whole externalHd.  Still no prievews in some folders.

So i basically just moved folders around and it worked.  Thanks for all your help guys, this community really is great. :)

---

### Post by gfd on 2006-09-21
> **ciscosurfer said:**
> @yeehawjared,

You can delete your icon cache and start clean...see if that helps.

Open Nautilus, go to View > Show hidden files 
Click the directory called .thumbnails
You can then open 'fail', 'normal', or 'large' (if you have it) and delete all files within.  You can also just delete the directories (they get replaced when you open a directory with pictures, videos, etc.)

Excellent, that did it for me.
Ubuntu had cached the thumbnails before I installed the codecs. Thats's why I couldn't see them.
All is fine now. 

Thank you!

---

### Post by gfd on 2006-09-21
> **Anduu said:**
> 
From the panel menu go to System>Preferences>File Management and select the preview tab.

I don't get that option in my Preferences menu.
Do I have to do something to enable it?

I just get: 
> Desktop Background
> Font
> Keyboard 
etc.

-- EDIT
I found it. It's hidden by default. I had to enable it through Alacarte.

---

### Post by ixus_123 on 2006-12-02
That seems like just what I'm after. I noticed in mine that a lot of thumbs were from a pictures directory I have that has well over 1500 pictures.  

The number of thumbs I had was just under 2000 even though I should have many more - if you include the pictures folder. Is there an upper limit to how many thumbs nautilus an store & if so, can it be changed?

> **ciscosurfer said:**
> @yeehawjared,

You can delete your icon cache and start clean...see if that helps.

Open Nautilus, go to View > Show hidden files 
Click the directory called .thumbnails
You can then open 'fail', 'normal', or 'large' (if you have it) and delete all files within.  You can also just delete the directories (they get replaced when you open a directory with pictures, videos, etc.)

---

### Post by ciscosurfer on 2006-12-02
> **ixus_123 said:**
> That seems like just what I'm after. I noticed in mine that a lot of thumbs were from a pictures directory I have that has well over 1500 pictures.  

The number of thumbs I had was just under 2000 even though I should have many more - if you include the pictures folder. Is there an upper limit to how many thumbs nautilus an store & if so, can it be changed?I don't know of any limit per se, but you can check the Preferences under an open Nautilus window (Edit > Preferences).  You can also look around inside **gconf-editor **(type this in a terminal or ALT-F2) to see if there are limits there.

---

### Post by sandervdv on 2008-05-26
Sollution is simple: install totem-gstreamer package.

---

