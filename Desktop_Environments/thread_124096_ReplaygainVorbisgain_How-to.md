---
title: "Replaygain/Vorbisgain How-to?"
date: 2006-01-31
forum: Desktop Environments
---

### Post by nmatheis on 2006-01-31
Hello
I'm wondering if there's a good program under Linux to implement Replaygain for audio tracks, like the simple to use Replaygain settings in Foobar in Windows?  Or at least like MP3-Gain?  I'd like to rip CDs as FLAC files for archiving, use Soundconvertor to convert to Ogg and Replaygain the resulting Ogg files.  If anyone knows of a good GUI to do this or at least give me a crash-course in doing this via the command-line.  I did install Vorbisgain but haven't used it from the command-line before - I always used one of Speek's frontends for Windows. 
Thanks!
Nikolaus

---

### Post by nmatheis on 2006-02-01
figured it out for both mp3gain and vorbisgain

---

### Post by skralljt on 2006-10-09
And how did you figure that out?  I see mp3gain and vorbisgain are in synaptic package manager but aacgain is nowhere to be found.  Also, the program replaygain itself is not found in synaptic!  Did you compile these yourself?

EDIT:  In order to set up aacgain, I have discovered that the easiest solution is to go to rarewares.com, click on debian, and follow all of the directions relating to installing extra repositories of xmilax and Christian Marrilat (sp?), and then install this stuff.  If you are new to linux, don't make the same mistake I did and leave these repositories enabled because then when you do dist-upgrades, you will find your entire system is in experimental mode, and very unstable!  I ended up without a working x system, and had to reinstall.  To avoid this but still get replaygain for aac and a million other great programs, install all the stuff from rarewares you want and then comment out the repositories when you are done.

---

