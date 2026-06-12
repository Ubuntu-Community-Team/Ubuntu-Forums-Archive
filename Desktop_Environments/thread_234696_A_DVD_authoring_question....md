---
title: "A DVD authoring question..."
date: 2006-08-11
forum: Desktop Environments
---

### Post by mmcmonster on 2006-08-11
I created a video with kino that I would like to put on a DVD.  I got as far as creating a .mpeg file.  The file properties say that the video codec is a MPEG video file (libmpeg2) with a mpeg audio layer 2 (lib: MAD) audio codec.

Suppose the file is called video1.mpeg.  How would I create a DVD .iso from this?

I tried googling for this a few times, but hit too many false positives by mentioning mpeg and mpeg2. :-(

---

### Post by andlinux21 on 2006-08-11
not sure if it will help any but you may want to check out [http://www.vcdhelp.com]("http://www.vcdhelp.com")it has a lot of good info on video converting, and authoring.

---

### Post by mmcmonster on 2006-08-11
Thanks for the website.

Unfortunately, all the how-tos in the DVD authoring section there that I have taken a look at so far are MSWindows based, and a good number of them use tmpgenc, which is a non-free application. :-(

Any other ideas?  I thought it should be easy, since the file is already mpeg2 encoded. :-(

---

### Post by mmcmonster on 2006-08-12
To answer my own question, [DVD Styler]("http://dvdstyler.sourceforge.net/") seems to work great.  As a bonus, .debs of the latest release (1.5 beta 5, actually) are available on the site so no need to get out your build tools.

---

### Post by mmcmonster on 2006-08-12
For others that want to use dvdauthor directly to author their DVDs, a useful site is the [documentation for dvdauthor]("http://dvdauthor.sourceforge.net/doc/index.html"), especially the [page]("http://dvdauthor.sourceforge.net/doc/ex-title.html#AEN37") with sample .xml files for 1 or more titles.

---

### Post by Ocxic on 2006-08-12
I use tovid, google it for a download.
it works pretty well for me.
if for some reason it doesn't work after it has completed to creation process, you must add the force option in tovid's config file. you'll have to google that too for instructions, i havn't use tovid for a bit now and can't remember exaclty where it is. you may have to create it.

---

### Post by mmcmonster on 2006-08-12
I tried [tovid]("http://tovid.wikia.com/wiki/Main_Page") a few times, but never was able to create a DVD .iso properly with it.  I played around with the commands that tovid sent to the lower-level commands that it uses, with lots of crashes to show for it.  I even used the directions from [a recent post to this forum]("http://www.ubuntuforums.org/showthread.php?t=183936"), without any joy. :-(

My next choice, if DVD styler didn't work was going to be ['Q' DVD-Author]("http://qdvdauthor.sourceforge.net/"), but I guess I dodged that bullet. :-)

---

### Post by DCM36 on 2006-08-12
What about DeVeDe? I use it every now and again and haven't had any problems with it. Check it out [here]("http://www.rastersoft.com/programas/devede.html").

---

### Post by mmcmonster on 2006-08-12
That's what I like about these forums - You start mentioning all the stuff you know about a problem, and someone else comes up with something you never heard of before. ;-)

I'll keep DeVeDe in my bookmarks (along with dvdauthor, DVD styler, 'Q' DVD Author, and Tovid) in case I need it in the future. :-)

---

