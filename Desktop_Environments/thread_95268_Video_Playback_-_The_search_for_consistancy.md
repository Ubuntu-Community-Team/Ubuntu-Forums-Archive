---
title: "Video Playback - The search for consistancy"
date: 2005-11-26
forum: Desktop Environments
---

### Post by Fillepe on 2005-11-26
This post is the result of a couple of hours of trying various things to see what works and what doesn't. Hope fully it will turn into a definition of what works best in what situation. If (and that is a HUGE if) any good comes of it it may be turned in to a Howto.

**Goal:** To be able to open all types of videos in the same program and have them play reliably with good quality and proper audio syncing.

The kicker with this is the audio syncing which seems to be inordanitly difficult for some players to handle.

**Potential programs for use:** Totem-gstreamer, Totem-xine, Mplayer, Realplayer

**Totem-gstreamer:** Although it is the way of the future it is currently completely useless for vidoe playback. This should change with the release of gstreamer-0.9 in the future. 

Verdict: :( 

**Totem-xine:** Shows promise however some unresolvable issues prevented final adoption. It is able to play almost all video streams but there is jittery playback on some .wmv streams. I would however be interested to hear the experiences of others with this. Also has an issues with stretching videos to widescreen scope (See attachment).  The general consensus seems to be that this is a good solution although it does not work for me.

Verdict: :???:

**Mplayer:** IMHO the best all round solution. Is capable of playing all video streams but cannot maintain sync between audio/video on real video files. Personally I like the lack of a user interface. To make mplayer play real video files first you need to install real player. 
This can be done from here:  [http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner](http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner)

Install realplayer

```

chmod +x <realplayer install file>
sudo ./<real player install file>

```

The installer will ask where to install RP to, remeber the location you specify. I used /opt/realPlayer. Then copy all of the files from the plugins directory in to /usr/lib/win32.

```

cd /opt/realPlayer
cp plugins/* /usr/lib/win32

```

If /usr/lib/win32 does not exist you need to install the win32 codecs.

Verdict: :???: 

**Realplayer:** Does not play any video files other than real video.

Verdict: :(


**Conclusions:** For me the best combination is totem completely uninstalled and to use a combination of Mplayer and RealPlayer.

Some of the many and varied problems that I have encountered that completely removing totem of any flavor a) disables video previews in nautilus and b) uninstalls Rhythmbox. If totem is left installed then it messes with the file associations in nautilus with Mplayer.

If anybody has a solution to the totem-xine scope problem, mplayer real video syncing, how to concretely set nautilus file associations or anything else I may have missed then post them please.

---

### Post by Keffin on 2005-11-26
Totem is the program that generates the nautilus previews for video files, so yes they will break if you completely remove totem. I don't know why rhythmbox is removed though. You should be able to change the preferred app for certain file types by right clicking the file then going to properties then the open with tab. It works for me.

As for totem-xine having issues with wmv sync, I have never had this problem. I have the win32codecs installed, maybe totem (xine) isn't seeing yours for some reason.

---

