---
title: "[B]Rhythmbox Trouble after Dapper Upgrade[/B]"
date: 2006-06-01
forum: Desktop Environments
---

### Post by blue_thunder on 2006-06-01
I just upgraded to dapper from breezy, and things seemed to be running smoothly until I tried to start playing music. Everything seemed to load into Rhythmbox, but then when I tried to play a song it raced through all the titles on the album leaving little error signs to the left of each track. When I clicked the sign I got an error message saying, "Playback Error: Internal data flow error."

Afterwards I tried deleting one album and then adding it again, and it wouldn't add. I've been able to play mp3s with xine and mplayer, but Rhythmbox doesn't seem to work. Help would be greatly appreciated.

---

### Post by 12quality on 2006-06-01
I have the exact same problem.  I'll let you know if I find a solution. Will you do the same for me?

---

### Post by Rackerz on 2006-06-01
Have you tried un-installing it? Also have you installed all multimedia codecs, it usually only does that if the codecs haven't been correctly installed.

---

### Post by emperor on 2006-06-02
[quote=blue_thunder]I just upgraded to dapper from breezy, and things seemed to be running smoothly until I tried to start playing music. Everything seemed to load into Rhythmbox, but then when I tried to play a song it raced through all the titles on the album leaving little error signs to the left of each track. When I clicked the sign I got an error message saying, "Playback Error: Internal data flow error."

Afterwards I tried deleting one album and then adding it again, and it wouldn't add. I've been able to play mp3s with xine and mplayer, but Rhythmbox doesn't seem to work. Help would be greatly appreciated.[/quote] 

After upgrading to dapper, I found that gstreamer-0.8 was still installed along with gstreamer-0.10. Removing all gstreamer-0.8 packages, adding some gstreamer-0.10-plugins, and then rebooting solved the problem for me!

---

### Post by 12quality on 2006-06-03
Much like "emperor,"  I found the problem was gstreamer, but once I installed the correct packages, it worked without a reboot.

Go into synaptic package manager (System > Administration > Synaptic Package Manager), and do a search for gstreamer.  Install gstreamer0.10-fluendo-mp3 and gstreamer0.10-ffmpeg, plus look around and see if there arre any other packages that may be useful for you, like gstreamer0.10-pitfdll and gstreamer0.10-fluendo-mpegdemux.

My guess from looking at my installed packages is that the Dapper version Rythbox must use gstreamer 10, where it previously must have used gstreamer 8.  It looks like these plugins didn't get added when gstreamer was upgraded along with the rest of Ubuntu. 

Summary-

Install plugins for gstreamer:
```
sudo aptitude install gstreamer0.10-fluendo-mp3 gstreamer0.10-ffmpeg
```

---

### Post by Garyu on 2006-06-09
wow, that really worked. :) thanks a lot! =)

I was actually browsing for missing codecs after the upgrade but only searched for "mp3". I find it kind of strange that ALL other players (movie and sound) would play my mp3's except for Rhythmbox. Also, I was a bit confused that some songs would play, but now I discovered that they were in .ogg format :-\"

---

### Post by goodfella on 2006-06-19
[QUOTE=12quality]Much like "emperor,"  I found the problem was gstreamer, but once I installed the correct packages, it worked without a reboot.

Go into synaptic package manager (System > Administration > Synaptic Package Manager), and do a search for gstreamer.  Install gstreamer0.10-fluendo-mp3 and gstreamer0.10-ffmpeg, plus look around and see if there arre any other packages that may be useful for you, like gstreamer0.10-pitfdll and gstreamer0.10-fluendo-mpegdemux.

My guess from looking at my installed packages is that the Dapper version Rythbox must use gstreamer 10, where it previously must have used gstreamer 8.  It looks like these plugins didn't get added when gstreamer was upgraded along with the rest of Ubuntu. 

Summary-

Install plugins for gstreamer:
```
sudo aptitude install gstreamer0.10-fluendo-mp3 gstreamer0.10-ffmpeg
```[/QUOTE]

Yeah I had the same problem and this fixed it perfectly.  Thanks :)

---

