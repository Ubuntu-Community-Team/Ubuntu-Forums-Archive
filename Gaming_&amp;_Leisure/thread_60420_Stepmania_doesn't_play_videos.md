---
title: "Stepmania doesn't play videos"
date: 2005-08-27
forum: Gaming &amp; Leisure
---

### Post by GreyFox503 on 2005-08-27
Hey guys.  I have Stepmania 3.9 rc3 installed, and I had to install a couple extra packages to get it to load, but for the most part its ok.  It doesn't give any errors on startup or exit and it plays most songs fine.

But, whenever I play a song with a video (I believe they are *.avi files encoded in MPEG2), the program shows the "event mode" screen, then before the stars would normally go across the screen to begin the song, the game very abruptly ends without warning.  I am instantly back at the desktop.

Here is a list of the packages I installed specifically for stepmania in order to make it work (without these, the game would not even load at all):

libmad0
lua_5.0.2-3_i386.deb  (local)
libffmpeg0.4.9cvs_0.4.9cvs-1mdk_i386.deb  (local)
libpng3 

It generates a debug file after it crashes, which I have attached (see below).


As you can see, I was trying to play MGS2, which does have a video that works because (you saw this coming) it work in Windows.

BTW: I can view this video using totem or xine just fine.

Anyone have any experience with stepmania specifically about which other packages I need, or is it something else I need to change?

If you don't know about Stepmania, any suggestions would still be welcome.

---

### Post by anacron on 2005-09-24
I can't see my backround-videos either right now, but my stepmania won't close even there is video in the song, so i don't really care about it.  ;-)  

Anyway videofiles in stepmania aren't usually mpeg2, they are divx encoded one's, so try installing [W32 codecs](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restrictedFormats%29) and stuff like that in order to make them work? Also are you using the normal rc3.9 or [stepmania online](http://www.stepmaniaonline.com/)  one?

sorry i can't help much, but i hope this helps you to find out the issue

---

