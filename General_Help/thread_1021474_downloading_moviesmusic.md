---
title: "downloading movies/music"
date: 2008-12-25
forum: General Help
---

### Post by ahebuki on 2008-12-25
Hey, I'm new to Linux. I have recently installed the latest version of Ubuntu(64-bit version). 

One of the things I use my computer for is downloading movies and music. I do this via itunes(mostly movies/tv series). Now I need to find an alternative to itunes as it doesn't work with linux.(I did try Wine but just got errors at the end of the install saying 'encountered errors, so no changes were made' or something to that effect.)

Any suggestions would be great.

---

### Post by socrazy143 on 2008-12-25
Amarok is a good manager of the music and vuze is a good all purpose player as well.  The Magnatunes on Amarok doesn't have much in the way of mainstream (that I could tell) but you could always purchase your music from places other than a built in mechanism like websites and then you would not be locked into DRM.

Another alternative albeit drastic is to load VMWare Server 2 on to your Ubuntu Machine and create an XP virtual machine to manage your music via ITunes.

---

### Post by pyromanic123boom on 2008-12-25
Can't you use the itunes store in a web browser? I thought that it just was integrated into itunes so the music could be localized.

---

### Post by socrazy143 on 2008-12-25
So I'm dinking around with Wine and ITunes and it looks like I got it working somewhat.  In fact this post might be more useful on a wine forum rather than here.

I noticed the install blows up just after Quicktime is installed.  I also noticed that Quicktime does get installed successfully.  I did some searching and found someone that had packaged ITunes 6 without Quicktime and loaded it up via Wine.  Wine froze up at the end of the install but installed itunes successfully (I use that word very loosely).

I'm working on getting it to recognize my new Nano and might see if it will recognize the old one.  My limited understanding of the hardware process has slowed me up but my urge to fix until broken completely keeps me going.  :D

---

### Post by socrazy143 on 2008-12-25
I found a site that helped me get iTunes up and running, I even got my nano to sync up.

[http://www.linuxscrew.com/2008/12/15/use-itunes-in-linux-including-apple-music-store/](http://www.linuxscrew.com/2008/12/15/use-itunes-in-linux-including-apple-music-store/)

CAREFULLY read the directions, take your time, be patient, blah blah blah.  To get your IPOD recognized plug the IPOD in and when it prompts you to pick a program to use choose other and in the Command box type in:

<CODE>wine /home/YOURUSERNAME/.wine/c_drive/Program\ Files/iTunes/itunes.exe</CODE>

Note the \ after Program.  It is necessary because of the break and not a mistype.

It isn't perfect and to be honest I don't plan to use it.  I just like the adventure of getting it to work.  I like Amarok and Vuze just fine and RhythmBOX looks good too (haven't used it much yet).

---

### Post by ahebuki on 2008-12-26
Yeah, followed that link and looks promising. Trying to get it worked out now. 

Thanks All!

---

### Post by cditty on 2008-12-27
Can anyone offer any more advice on this?  

<CODE>wine /home/YOURUSERNAME/.wine/c_drive/Program\ Files/iTunes/itunes.exe</CODE>

I tried it and itunes won't load.  When I try again, and look at the application drop down box, it just lists wine and nothing else.

Any tips?

---

