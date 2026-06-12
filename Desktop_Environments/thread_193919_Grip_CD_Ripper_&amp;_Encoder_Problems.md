---
title: "Grip CD Ripper &amp; Encoder Problems"
date: 2006-06-10
forum: Desktop Environments
---

### Post by abbot on 2006-06-10
I've been using Grip since I started using Linux and I think that it's no doubt the best and most customizable CD ripping program.  I've been having trouble with it on Dapper though.  

The first time I opened the default version from the Dapper repositories I get a message talking about how it's a testing version and that if I experience problems I should use a stable version.  Shouldn't the stable version be the one that's in the main Dapper repository?  I didn't think too much of it untill I discovered that it doesn't work.  I'm using lame for encoding but it seems like its just skipping the encoding step and putting broken files in the finished folder as soon as the ripping step is done.

So my question is does anyone know if this is really a problem with Grip or if it is Lame with the problem.  How do I go about getting the stable version of Grip since it's not in the repository?

Thanks.

---

### Post by timetunnel on 2006-06-11
I remember getting the same message when I had installed Breezy, and now again in Dapper. But I never had any problems with it. I ripped my whole CD collection to MP3 with lame and Grip in Breezy. And being on Dapper now, I've just finished ripping all CDs again with Grip to OggVorbis format.

You sure that your command line configuration for lame in Grip is not messed up?

---

### Post by abbot on 2006-06-11
i would use ogg, but my archos mp3 player doesn't support it.  these are my encoder settings:

Executable: /usr/bin/lame
Command-Line: -h -b %b %w %m
Extension: mp3
Format: ~/Multimedia/Rips/%A - %d - %y/%t - %a - %n.mp3

---

### Post by timetunnel on 2006-06-11
I just ripped a track and encoded it with lame successfully, using the settings you provided above. So, Grip and lame seem to work generally.

---

### Post by shrimphead on 2006-06-11
sounds like a stupid question but do you actually have lame installed? IIRC Grip will let you select lame in the options without actually checking if the binary is there.

---

### Post by abbot on 2006-06-12
yeah i do.  i actually went and found the bin file in /usr/bin before i filled in the executable line in the settings.

---

### Post by abbot on 2006-06-12
Hmm.  It seems to be working now, even though I didn't change anything.  The encode % bar is actually moving rather than just dumping a broken file in the finished folder right after it was ripped.  The finished files are working.  Odd.

---

### Post by abbot on 2006-06-14
Actually, what I think it may have been a couple things in my configuration.  First I had the % sign on the wrong side of my letters in the file name format fields.  I also accidentally had the mp3 bitrate set to 198 instead of 192 and lame didn't like that.  Seems to be working now, except that it's cutting off the encoding before its done with the whole cd every once in a while.  If it keeps doing it I'll try to figure out what that problem is.

---

### Post by abbot on 2006-07-03
OK.  I guess my problems aren't all gone.  Lame seems to be causing X to crash maybe 4 out of 5 times I try to rip a CD.  It usually happens about 5 minutes into the ripping/encoding process.  I figure it's a lame problem because I've tried using lame with other CD ripping programs with the same result.  It's either X completly freezes and i can't even move my mouse pointer, or it boots me out to the log in screen.

Is there a different encoder that I can try?

---

