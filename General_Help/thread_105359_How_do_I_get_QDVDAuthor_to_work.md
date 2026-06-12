---
title: "How do I get QDVDAuthor to work?"
date: 2005-12-18
forum: General Help
---

### Post by BabaFree on 2005-12-18
Does anyone know of a good tutorial on getting QDVDAuthor to work?  I googled but didn't come up with anything.  Also didn't find anything specific here.  What I'm trying to do is capture the video from my Digital camcorder and then burn it onto a viewable DVD.  So far, no luck.  Any help would be greatly appreciated, as both sets of grandparents have been wanting dvd's of my son for months now :)  Thanks in advance.
God Bless,
Brandon

---

### Post by BabaFree on 2005-12-21
I've gotten Kino to convert my DV captured video into MPEG2 format that QdvdAuthor uses, but when I try to run the program, every command seems to generate some kind of error.  Is this just a bad program?  Or is there something I'm just not getting?  Thanks,
BabaFree

---

### Post by Emerzen on 2005-12-21
I ran around in circles trying to find a DVD authoring app that worked, and QDVDAuthor was one of the most difficult.  The error is apparently w/ the version of MJPEGtools that Breezy has in the repositories.  If you add one of the Debian repositories and go back to an older version of MJPEG tools, it should work.  I found QDVDAuthor way to difficult, but was able to get further w/ a program called DVDStyler.  Same thing applies here, you'll have to do the MJPEG tools trick to get it to work, but it does work w/ this trick...most of the time.  So:

To get the old version of MJPEGtools, follow this thread-> [http://www.ubuntuforums.org/showthread.php?t=79715&highlight=mjpegtools](http://www.ubuntuforums.org/showthread.php?t=79715&highlight=mjpegtools)

Then search for DVDStyler (Google) and you'll have to download and compile it w/ the old version of MJPEGtools.  Then it should work.  

Another option that may work is to use a tool called Tovid.  This app is less flash but seemed to work most of the time if you follow their installation instructions.  Again, google Tovid and you should come up w/ the site.  And, again, you'll have to compile it yourself.  

To be honest, I pretty much gave up on this in Linux and reverted back to Nero in XP.  I've been anxiously awaiting for an update to MJPEGtools, so I can try to get it working more consistently with Ubuntu.

---

### Post by bionnaki on 2005-12-21
tovid is excellent. the key is to apt-get tovid-gui
the gui is perfect.

---

