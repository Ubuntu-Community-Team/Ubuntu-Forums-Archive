---
title: "AVI videos are clogging in VLC after the update from 8.10 to 9.04"
date: 2009-02-07
forum: General Help
---

### Post by Jailbird on 2009-02-07
The topic title says it all. It's maybe a VLC issue, but AVIs are jamming every 3-4 seconds after the update from 8.10 to 9.04. Anyone familiar with the issue? Thanks for your help in advance!

---

### Post by Svensk023 on 2009-02-07
what window manager are you using, compiz or metacity?

---

### Post by Jailbird on 2009-02-07
Compiz, but the visual effects are all turned off (if that means anything).

---

### Post by mb_webguy on 2009-02-07
This is the sort of thing that keeps me from upgrading to pre-release versions. ;)

I looked around for PPAs or debs for VLC compiled for Jaunty, in case the ones in the repository have a glitch that's causing the problem, but I couldn't find any.  Plenty for Hardy and Intrepid, but none for Jaunty.  Maybe you could try the Intrepid debs from [GetDeb]("http://archive.getdeb.net/dump/intrepid/vlc/")?

---

### Post by jocko on 2009-02-07
I'm not sure this is the same, but vlc (v0.9.8a) in 9.04 seem to have a problem for me as well.
Movies play mostly fine, but every now and then the image freezes up for a few seconds while the audio continues.
When the image starts again it first just updates part of the image (so some things starts moving again in the mostly frozen image, looking really weird). After a second or so the entire image is updated and moves in sync with the audio track again.
Another problem (which I think is related) is that the sound from mp3's are very choppy (frequent very short silent periods and a few cracks and pops...).

I've managed to work around both of these problems by increasing vlc's file cache from default 300ms to 5000ms.
In vlc: Tools-->Preferences-->Access modules-->File; change from 300 to 5000.

Now vlc plays both movies and mp3's without problems, with only one annoyance: vlc now reads every file for 5 seconds (instead of 0.3) before it actually starts to play.

---

### Post by Svensk023 on 2009-02-07
> **Jailbird said:**
> Compiz, but the visual effects are all turned off (if that means anything).

well you could try using metacity, but unless your trying to help with bugs and major issues, i wouldn't use pre-releases' unless you're prepared to deal with a lot of pain in the rear

---

### Post by Jailbird on 2009-02-07
Thank you for your reactions!
Yep, just realized that the MP3 playback is having the same problems. For me it just hangs up for a short time every second or two. Movie Player works fine with all media files, so I guess it must be a VLC issue. 
I just opened a topic on the VLC forums as well, perhaps they could tell more. If nothing else helps, I'll try Metacity :)

---

### Post by zork2 on 2009-02-08
sudo apt-get install vlc-plugin-pulse fixed the problem for me.

---

### Post by Jailbird on 2009-02-08
> **zork2 said:**
> sudo apt-get install vlc-plugin-pulse fixed the problem for me.

Unfortunately not for me :(

---

### Post by personjerry on 2009-02-08
new sticky; this should be in the jaunty section

---

