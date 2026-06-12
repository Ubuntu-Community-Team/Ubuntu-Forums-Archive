---
title: "Rhythmbox CDDB Fail"
date: 2011-05-24
forum: Desktop Environments
---

### Post by HRH_H_Crab on 2011-05-24
Lots of requests for help:

[http://ubuntuforums.org/showthread.php?t=1664485](http://ubuntuforums.org/showthread.php?t=1664485)
[http://ubuntuforums.org/showthread.php?t=1161017](http://ubuntuforums.org/showthread.php?t=1161017)
[http://ubuntuforums.org/showthread.php?t=1147610](http://ubuntuforums.org/showthread.php?t=1147610)

Don't seem to be many useful replies.
I'm sure this has worked for me before.
Anyone got any ideas?

For what its worth Banshee doesn't seem to have working CDDB lookup either.

---

### Post by mfearby on 2011-05-25
This is also driving me absolutely crazy. Rhythmbox's CDDB lookups are very infrequent these days. I tried installing a plugin I found linked from live.gnome.org, nothing (very poorly documented it was, too). Can't use ripperx because it refuses to let me include the track number in the resulting files (not good when you're ripping classical music where the sequence of tracks is important!), am currently using RipOff which does seem to be doing the job, but it's taking an eternity to rip the CD (20 minutes compared to about 5 with Rhythmbox on a good day). There's also the bug with ripperx not letting you rip sometimes beyond track 9.

My brother has been on my case lately to buy an iMac. Not a day seems to go by where he's not singing Apple's virtues. I have to say that if I can't rip my CDs to MP3 reliably, then I may very well give in and just buy one. There's also the fact most desktop environments seem to be going the way of the dumbed-down plastic spoon treatment given to mental patients at risk of hurting themselves. Not even Apple insults their users as much as GNOME 3/Unity!

The only good thing about RipOff taking it's time ripping a CD is the silence, I guess :-)

---

### Post by HRH_H_Crab on 2011-05-25
Bump.

---

### Post by dreadmo on 2011-05-25
The problem seems to be a missing Musicbrainz library. I installed Sound-Juicer as a (sort of) workaround and it in turn installed libmusicbrainz3-6.
The data showed up properly in Sound Juicer. Then I opened Rhythmbox and the data lookup was back to normal. Try installing libmusicbrainz3-6 (or Sound Juicer) through Synaptic or apt-get and see if it works for you as it did for me.

---

### Post by dreadmo on 2011-05-25
Followup: the solution above worked exactly one time. I've inserted other CDs and gotten nothing. Sound Juicer produces this message: "Retrieving track listing...please wait", but nothing happens. I'm guessing that this has something to do with some recent reconfigurations at Musicbrainz, but I'm just guessing.

---

### Post by brewzka on 2011-05-25
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/787475](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/787475)

Yeah it doesn't work. I posted that bug.


May 24th, 2011
  On my two Ubuntu machines Rhythmbox is not fetching album tagging  information from MusicBrainz even though the information exists on the  MusicBrainz database. I checked with the picard program I had on the  machines. The CD lookup revealed the tagging information in picard.
  Here are my machines:
 

> Pentium D
Memory 2.9 GiB
 9.10 [kernel 2.6.31-23-generic]
Rythmbox 0.12.5
 libdiscid0   [Version: 0.1.0-1]
libmusicbrainz4c2a   [Version: 2.1.5-2ubuntu1]
picard   [Version: 0.11-2ubuntu3]
 ||||||
 Core 2 Duo
Memory: 2.0 GiB
 10.04 [kernel 2.6.32-31-generic]
Rythmbox 0.12.8
 libdiscid0   [Version: 0.2.2-1]
picard   [Version: 0.12.1-0ubuntu1]
libmusicbrainz4c2a   [Version: 2.1.5-4]


Just ran the --debug command and here is the output.
>                   This CD could not be queried: Cannot find musicbrainz pages on server. Check your server name and port settings.
(03:33:31) [0x87eb028] [metadata_cb] rb-audiocd-source.c:767: ignoring CD metadata from fallback source

        


To reproduce follow these steps:
> 
1. Insert a well known cd into the tray
 2. Run rhythmbox --debug
 3. Go to the CD section under the area titled "Devices"
 4. Hit the "Reload Album Information" button.
 5. Look at debug information.


Additionally banshee is having the same problem according to many users.

---

### Post by mia1dolfan on 2011-05-25
I believe Ubuntu ( Rhythmbox / Banshee / Sound Juicer ) doesn't support CDDB, they use MusicBrainz for tagging CDs / MP3s.  This is because CDDB is commercial.  There's a old, un-updated plugin for Rhythmbox for CDDB support, but it doesn't appear to work anymore.  Your going to have to install another utility from the software center to do CDDB lookups.  Don't expect Ubuntu to include CDDB support anytime soon.

I have experience with ripperX, and ripoff, both in the repository that have CDDB support, there are other utilities in there as well that will do the job for Kubuntu, Xubuntu, and the from the console.

Install lame if you want to encode to MP3
```
sudo apt-get install lame
```

For RipperX console install:
```
sudo apt-get install ripperx
```

In the configuration of RipperX, under General you probably will want to change the Target Directory from ./ to ./Music - In the Mp3 tab pick OggVorbis encoder, or if you to encode to MP3, then select Lame MP3 Encoder in the same selection box (you installed lame, right?).

For ripoff console install:
```
sudo apt-get install ripoff
```

In the preferences of ripoff, change the "ripoff output folder" to ~/Music.  In the plugins tab select Lame Encoder with you want to encode in MP3 format (you installed lame, right?)

:guitar:
Rock On!

---

### Post by mfearby on 2011-05-26
I already have libmusicbrainz3 installed, and also didn't know that CDDB is commerical. I don't care what Rhythmbox uses for its track information, I just want it to work :-)

---

### Post by brewzka on 2011-05-26
Yeah at the moment MusicBrainz is unaccessible via Rythmbox.

---

### Post by dreadmo on 2011-05-27
Thread really should be called "Rhythmbox Musicbrainz Fail."

Information on the bug can be found here: [http://blog.musicbrainz.org/?p=839](http://blog.musicbrainz.org/?p=839) . See particularly the last (most recent) entry.

In short, to quote from *Cool Hand Luke*, "What we have here is a failure to communicate."

---

### Post by aextance on 2011-05-29
Anyone who's on Launchpad probably ought to sign up and say this bug affects them. Hopefully that will get this fixed more quickly - although perhaps not over Memorial Day weekend. Is there anywhere in the world that ISN'T having holidays this weekend? Alternatively, is there a way we can change the packaging to fix this ourselves?

---

### Post by mfearby on 2011-06-04
I have to say that I'm rather happy with RipOff now. It's quiet (albeit slower) but there are also less interruptions to my work, so it's not as noisy or needy as ripping CDs with Rhythmbox, and it has excellent CDDB functionality :-) 

I never did like Rhythmbox much, anyway. It won't remember column widths or much in the way of GUI preferences, so I'm glad to see the back of it, actually.

---

### Post by karrank% on 2011-06-08
having the exact same problem with soundjuicer, a patch I'll link here seems to work for the moment, maybe could be applied to rhythmbox? anywho, give this a shot.

[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/455461]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/455461")

---

### Post by bloozguy on 2011-06-11
Same thing with "Banshee".
The problem is MusicBrainz which I am starting to hate.

 I wish there was a way to use freedb.org it always worked and allowed you seamlessly to have a local metadata DB as well when using good ol' "grip".

---

### Post by T_W on 2011-06-14
*Sigh*

I literally **just** sat down to rerip my entire CD collection at a higher bit rate.  

So now 10.04 LTS is worthless for CD ripping :(

---

### Post by zippyzippy on 2011-10-25
This has been going on for how long now????

I chose 10.04 LTS for my customers interested in using Linux rather than Microsoft. I cannot retroactively go back and fix all clients' machines upon which this problem now resides. I've been hoping this problem would be solved ... eventually. Apparently not.

RipperX and Ripoff are not good workarounds. Personally, I have a folder structure that I'm not going to change because LTS has a broken application. No, we are going to be installing Fedora Core from here on out. I just need less calls from my clients after the fact, you know? I get enough of that from the MS clients.

---

### Post by Schrammel on 2012-02-16
So now it is middle of february and this bug still exists.
This is ridiculous.

---

### Post by hic3456 on 2012-03-24
Has this been fixed yet for Maverick (10.10)?

This is somehow ridiculous, folks - the change by MusicBrainz was fully reasonable, and the fix probably trivial: a full year on and Rhytmbox is still broken.

As others have said, this is a functionality we take for granted on our Macs (much as I personally hate iTunes) and even Windoze machines.... and which we used to have on our Ubuntu boxes.

Probably a one-day fix, and it's been here for almost a year now?

---

### Post by Mediosordo on 2012-04-03
Would love to have this fixed... It's quite incredible that the most popular Ubuntu media player can't get it's tags automaticaly fixed.

---

