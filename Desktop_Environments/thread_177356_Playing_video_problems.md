---
title: "Playing video problems"
date: 2006-05-16
forum: Desktop Environments
---

### Post by kate on 2006-05-16
At present, I have both xine and gstreamer engines installed. With Totem, I can't get any of my media files (avi, mpeg or mp3) to play, with Amarok, I can get the sound to play fine. With Kaffeine, the sound files play, and so do the soundtracks of my avi and mpeg files, but the visuals are a green thing with different flecks though it. I don't mind Totem not working, but I would like to know how to get visuals in Kaffiene. Please keep in mind I've been using Kubuntu for about three days (but I have used Ubuntu for a few months, but only doing what I need to do and nothing more).

Incase that it matters, it is the Xine that I am using as gstreamer does not wish to cooperate.

---

### Post by Sef on 2006-05-16
Have you downloaded the codecs?

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by kate on 2006-05-16
Yes, that's the first thing I did, but I still can't get visual.

---

### Post by kate on 2006-05-17
This still isn't resolved. Are people just out of ideas and should I just let this thread die?

---

### Post by wick on 2006-05-17
Hello all -

A new Ubuntu user here... almost everything is going swimmingly so far.  But I am also having MPEG video playback issues.  Sound is fine but picture is green/blue bars.  I have downloaded the codecs suggested at the Wiki page.

Might this be a hardware issue?  If so, where should I begin looking to solve that?

Thanks!

---

### Post by ZiLOG_Z80 on 2006-05-17
If its a hardware problem i would guess most likely down to video card, would help if you could both list your hardware setup just in case. and also which gfx card driver you are using

Have you tried changing the settings 
'System ->Preferences ->Multimedia Systems Selector

look in the video tab and change the output type

---

### Post by fadain on 2006-05-17
I am having the same problem, xine displays wierd colors while playing video. I am running kubuntu on a laptop, graphic card is intel integrated 900 series.

---

### Post by ronniet on 2006-05-17
I'm certainly _no_ linux expert but when i was running Hoary (now running Dapper) I used Mplayer (still do, with Dapper) with the codecs pack and i could view most files, even windows' wmv files.

I think you need to enable the multiverse? Then download Mplayer from there.

Then i made a directory in the /usr/lib/ called 'win32'.
Unzipped the codecs into there and Mplayer played anything i tossed at it...

**Good luck!**

---

### Post by link141 on 2006-05-17
I can't get Mpeg, AVI, MP3, WMA, or Quick Time files to play, even though I downloaded the MPEG and MP3 libraries and have MPlayer installed.  Thanks in advance for any support :).

---

### Post by cocox on 2006-05-18
for those who have Breezy and wants to view videos with win32 codecs in totem quickly!!!(flash guide)

sudo aptitude install  gstreamer0.8-plugins gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg

wget -c [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.4_i386.deb)

sudo dpkg -i w32codecs_20050412-0.4_i386.deb

sudo aptitude install totem-xine

;)

---

### Post by kate on 2006-05-18
I'm using an AMD Duron 750+ using the builtin graphics (please don't hurt me :( ).

---

### Post by fadain on 2006-05-18
Just installed mplayer and the result is the same. Output is in green/blue color... is it because of the integrated graphic driver ? I am using the 'i810' driver.

---

### Post by kate on 2006-05-19
Wow! MPlayer works really well! Thanks everyone! I hope the others get theirs working!

---

