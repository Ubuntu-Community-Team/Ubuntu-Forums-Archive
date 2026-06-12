---
title: "VLC Is Ugly"
date: 2005-10-14
forum: Desktop Environments
---

### Post by br00tal on 2005-10-14
Not sure why this happened, but my VLC player has recently lost it's visual appeal.  Meaning that it is freakin' ugly now!  I've had this happen to other GTK-based applications under Hoary, but this is the first one to do this with Breezy.  When I have RC1 of Breezy installed, VLC looked normal with proper text size and proper skin color **until** I downloaded an updated VLC package from the repository.

Now, I formatted and did a clean install of the official Breezy yesterday, and when I did an apt-get and installed VLC, it looked ugly like it did when I upgraded it on RC1.  So I'm assuming that the new package just looks this way?  Here's a screenshot of what I'm talking about:

[[IMG]http://img437.imageshack.us/img437/4623/screenshot9ex.th.png[/IMG]](http://img437.imageshack.us/my.php?image=screenshot9ex.png)

Notice the plain white border and large text on the VLC GUI.  Is there anything I can do to make it look like it used to, or am I going to have to deal with it?

By the by, so far this is the only thing I have found with Breezy that I've not liked.  Everything else (to my knowledge, anyway) works 100%.  Thanks for this great OS, Ubuntu Team!

Cheers,
Jesse

---

### Post by bored2k on 2005-10-14
VLC turned ugly after its last update (which was terrible). I would expect the nice GTK2 GUI to come back on the next vlc upgrade.

---

### Post by MaX on 2005-10-14
VLC is Fck:ed in Breezy.

---

### Post by deeek on 2005-10-14
You can always revert to the previous version!    (I sound like a broken record)

[www.umsl.edu/~dmwkt7/vlc_0.8.2-1ubuntu3_i386.deb]("http://www.umsl.edu/~dmwkt7/vlc_0.8.2-1ubuntu3_i386.deb")
[www.umsl.edu/~dmwkt7/wxvlc_0.8.2-1ubuntu3_i386.deb]("http://www.umsl.edu/~dmwkt7/wxvlc_0.8.2-1ubuntu3_i386.deb")

---

### Post by Goober on 2005-10-14
Try searching for VLC, I had to after my VLC randomly stopped working, and apparently an Update messed it up.  Now its back, working.  Some might not like it, but I actually prefer the current look.  Looks techno-weenie, as one of my teachers might say ;)

---

### Post by 12quality on 2005-10-14
I agree that vlc is ugly, but this can be rectified with skins.  VLC has some pretty skins on its website:

[LIST=1]
[*]Go to [http://www.videolan.org/vlc/download-skins2.html]("http://www.videolan.org/vlc/download-skins2.html") and download a pretty skin.
[*]Launch VLC in skins mode by typing ```
vlc -I skins2
```
[*]Immediately you should see the default skin, but it doesn't skin the video window.  Right-click on the vlc window > mouseover "Miscellaneous" > select "Preferences"
[*]In the selection on the left, click on "Interface". Click the arrow next to "Interface". Select "General". Under interface module, select "Skinnable Interface." Click "Save" and close this dialog box.
[*]In VLC, type ctrl-s. Locate the skin you downloaded and it should appear by default from then on.
[/LIST]

There might be an easier way to do this, but this should work.  And look how nice it can look. [IMG]http://duke.edu/~sds8/vlc_skin.jpg[/IMG] 
Note: this image was modified using gimp to have the contents of the screen visible rather than just the bluescreen one gets with the gnome screenshot utility.

---

### Post by Qrk on 2005-10-14
I tired changing skins and I get this error message

k-CRITICAL **: file gdkcolor.c: line 57 (gdk_colormap_new): assertion `visual != NULL' failed.
                Segmentation fault

when I try to run vlc in the terminal. Now I can't open it to change the skin back. Any ideas?

---

### Post by yjsoon on 2005-10-15
I like how I found this forum by searching for "vlc ugly" in distress. :p 

To answer Qrk: try deleting your .vlc directory in your home folder (unless you have any customisations you want to keep, in which case edit ~/.vlc/vlcrc).

---

### Post by fishfork on 2005-10-15
[QUOTE=deeek]You can always revert to the previous version!    (I sound like a broken record)

[www.umsl.edu/~dmwkt7/vlc_0.8.2-1ubuntu3_i386.deb]("http://www.umsl.edu/~dmwkt7/vlc_0.8.2-1ubuntu3_i386.deb")
[www.umsl.edu/~dmwkt7/wxvlc_0.8.2-1ubuntu3_i386.deb]("http://www.umsl.edu/~dmwkt7/wxvlc_0.8.2-1ubuntu3_i386.deb")[/QUOTE]

Appreciate you hosting these, but why not just get the debs from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) ?

---

### Post by br00tal on 2005-10-15
Thanks for the skins tip, but I noticed another thing...dvd::rip is frickin' nasty, too!  I think there's certain GTK apps that are just disgusting looking in Breezy.  There's got to be some sort of global cause of all this...right?  I wouldn't care so much, but dvd::rip won't fit on entirely on my screen with it's current appearance...the text is too large.  And when I tell it to exand to fill the desktop, it removes some of the buttons in order to do so.  Not sure what's causing this, but I hope it gets resolved relatively soon (or I hope I figure it out to tell all of you).

Cheers,
Jesse

---

### Post by Tasu on 2005-10-16
Indeesd it's ugly, but it seems thre are reasons for that, due to some problems with unicode that wxwidgets 2.6 have...

Look here for discussions:
[http://ubuntuforums.org/showthread.php?t=75322](http://ubuntuforums.org/showthread.php?t=75322)
[http://ubuntuforums.org/showthread.php?t=74308&highlight=vlc](http://ubuntuforums.org/showthread.php?t=74308&highlight=vlc)

---

### Post by lithorus on 2005-10-16
[QUOTE=Tasu]Indeesd it's ugly, but it seems thre are reasons for that, due to some problems with unicode that wxwidgets 2.6 have...

Look here for discussions:
[http://ubuntuforums.org/showthread.php?t=75322](http://ubuntuforums.org/showthread.php?t=75322)
[http://ubuntuforums.org/showthread.php?t=74308&highlight=vlc](http://ubuntuforums.org/showthread.php?t=74308&highlight=vlc)[/QUOTE]
I think the problem is that there is only a unicode release of wxwidgets 2.6 which requires the code to be unicode compatible. My guess is that the VLC code isn't written for unicode.

I recently made some non-unicode debs of wxwidgets 2.6 and will try to build VLC with them later.

---

