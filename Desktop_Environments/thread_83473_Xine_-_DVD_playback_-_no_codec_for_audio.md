---
title: "Xine - DVD playback - no codec for audio"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Chareos on 2005-10-28
**** UPDATE: please read my latest reply. If anyone is skilled in recompile xine (not to break amarok-xine and other related apps) the commmunity could get benefit of a more usable xine in Breezy. ****





Hi all,

I'm trying to get Xine working as was for Hoary.


Straight to the point, if I start xine as root my DVDs play fine.
If I start it as user xine works for menus, then - when track passes to AC3 multichannel - it stops complaining for no codecs found.

Is something changed with codec path ?

my particuar repositories:
[ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) debian sarge
[http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy extra-staging


I installed ffmpeg (in case...) a52, win32 codecs.


Thanks for suggestions
Fabio

:confused:

---

### Post by manicka on 2005-10-28
First, leaving the marillat repo is your sources list permanently will break ubuntu. Comment it out.

You could try the codecs packages available here
[http://ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs+easy](http://ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs+easy)

could you also start xine in a terminal and post any error messages

---

### Post by Chareos on 2005-10-29
Thanks for your reply.

Thinkering about it, launching in terminal gives no errors, only normal CSS KEY output (so all is fine with libdvdcss).

Then I found that my problem occours when movie starts (as I stated before) AND when I select Surround 5.1 as output for alsa - within xine.

Today I've noticed that
[http://sourceforge.net/mailarchive/forum.php?forum_id=3438&max_rows=25&style=nested&viewmonth=200506](http://sourceforge.net/mailarchive/forum.php?forum_id=3438&max_rows=25&style=nested&viewmonth=200506)

some months ago there was a problem with movies with menu in 2.0 and movie in 5.1 with exact problems I reported.
Late in the 'noon I'll check if breezy's xine version is the cursed one.
If that's so I'll require a bugfix (more recent version) or try to compile from source.

---

### Post by Chareos on 2005-10-29
Got it...

there's a 4 months old BUG in xine:
[https://sourceforge.net/tracker/?func=detail&atid=109655&aid=1226595&group_id=9655](https://sourceforge.net/tracker/?func=detail&atid=109655&aid=1226595&group_id=9655)

One of the most appreciate progression in Breezy is support for multiple audio streams (dmix) out of the box.
Unfortunately, xine is bugged with dmix.
Also they ALREADY found the solution, but since 4 months it's not applied yet.


I fear I'll have to patch the source and recompile for myself...

... or Breezy staff/collaborators could patch it as described in the link above and make an Ubuntu package ?


Fabio

---

### Post by Chareos on 2005-10-29
Just to inform I filed a bug to Ubuntu.
#18624

---

### Post by emuman on 2005-10-30
Change the device for stereo and mono in xine to e.g. "plug:surround51:0" or whatever you use. The problem with xine und dmix results in the change between stereo and 5.1 in menus/movie stream.

---

### Post by Chareos on 2005-10-31
Emuman, your trick did the job !

That way everything works. I didn't realize that plug:surround51.0 was useable there also.


Anyway this still to be a workaround. I made aware a xine developer of this bug AND of your workaround. Now he's on it (5 months later...)

Thanks, good job.

---

### Post by Chareos on 2005-10-31
Now I'm facing the incredible... xine looses setting for "stereo" every time I start it up...

---

### Post by superm1 on 2006-01-13
[quote=Chareos]Emuman, your trick did the job !

That way everything works. I didn't realize that plug:surround51.0 was useable there also.


Anyway this still to be a workaround. I made aware a xine developer of this bug AND of your workaround. Now he's on it (5 months later...)

Thanks, good job.[/quote]

Awesome workarond emuman.  Works for me on gentoo ~x86.  I wonder why this still isn't fixed upstream though?

---

### Post by russ1960 on 2006-03-11
I am a newbie - somebody walk me thru this change.  I get this error no matter which media player I use.   How do I make thi change?

Thanks

Russ

---

### Post by [S2] on 2006-12-02
> **russ1960 said:**
> I am a newbie - somebody walk me thru this change.  I get this error no matter which media player I use.   How do I make thi change?

edit the xine config file (~/.xine/config) and add two lines:

```
audio.device.alsa_default_device:plug:surround51:0
audio.device.alsa_front_device:plug:surround51:0
```

---

