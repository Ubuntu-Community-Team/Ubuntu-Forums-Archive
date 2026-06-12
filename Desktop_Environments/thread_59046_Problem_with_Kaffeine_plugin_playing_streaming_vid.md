---
title: "Problem with Kaffeine plugin playing streaming video"
date: 2005-08-22
forum: Desktop Environments
---

### Post by clehel on 2005-08-22
Hi,
I tried playing streaming video with both Firefox and Konqueror, using Kaffeine plugin. E.g. with Konqueror the Kaffeine starter plugin was invoked, that in turn opened Kaffeine, Kaffeine did some startup gimmicks, but here the action stopped. As next step, Kaffeine was started from command line with the URL of the videostream itself, and then it gave this long message. I don't know what part might be important, so I just copied all here, I am sorry, it is a little long.

Do you have any suggestion what to try/change? Thanks a lot in advance!


> clehel@apagepe:~$ kaffeine [http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl](http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl)
Main: XInitThreads()
[INFO] If Kaffeine hangs here run 'configure --with-xorg' and recompile/reinstall.
kaffeine: No DVB device found.
kaffeine: Window manager: KWin found
kaffeine: Kaffeine:: Try to load service: kaffeine_part
kaffeine: This is a KMediaPart...
kaffeine: KaffeinePart: Creating new KaffeinePart...
kaffeine: PlayList: add 1 items to playlist
kaffeine: PlayList: Check for kaffeine/noatun/m3u/pls/asx playlist
kaffeine: PlayList: Try loading kaffeine playlist
kaffeine: PlaylistImport: kaffeine: /home/clehel/.kde/share/apps/kaffeine/playlists/NEW.kaffeine
kaffeine: PlayList: add 1 items to playlist
kaffeine: KaffeinePart::openURL(): [http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl](http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl)
kaffeine: KaffeinePart: Got single track
kaffeine: KaffeinePart::slotPlay()
kaffeine: KXineWidget: Display aspect ratio (v/h): 1.00102
kaffeine: KXineWidget: Using xine version 1.0
kaffeine: KXineWidget: Post-init xine engine
kaffeine: KXineWidget: Use audio driver auto
kaffeine: KXineWidget: Use video driver auto
kaffeine: KXineWidget: Init video driver
kaffeine: KXineWidget: Init audio driver
kaffeine: KXineWidget: Init OSD
kaffeine: KXineWidget: Font for OSD: sans
kaffeine: KXineWidget: Unscaled OSD available
kaffeine: KXineWidget: xine init successful
kaffeine: KaffeinePart: load config
kaffeine: Set volume to: 100
kaffeine: KXineWidget: New visualization plugin: goom
kaffeine: PostFilter: Create Postprocessing Filter: tvtime
kaffeine: PostFilter: Parameter: method
kaffeine: PostFilter: Parameter: enabled
kaffeine: PostFilter: Parameter: pulldown
kaffeine: PostFilter: Parameter: framerate_mode
kaffeine: PostFilter: Parameter: judder_correction
kaffeine: PostFilter: Parameter: use_progressive_frame_flag
kaffeine: PostFilter: Parameter: chroma_filter
kaffeine: PostFilter: Parameter: cheap_mode
kaffeine: PostFilter: Get input
kaffeine: PostFilter: Get output
kaffeine: PostFilter: SetConfig tvtime:method=LinearBlend,enabled=1,pulldown=none,framerate_mode=half_top,judder_correction=0,use_progressive_frame_flag=1,chroma_filter=0,cheap_mode=1
kaffeine: PostFilter: Set parameter 'method' to value 'LinearBlend'
kaffeine: PostFilter: tvtime Apply integer value 2 on offset 0
kaffeine: PostFilter: Set parameter 'enabled' to value '1'
kaffeine: PostFilter: tvtime Apply integer value 1 on offset 4
kaffeine: PostFilter: Set parameter 'pulldown' to value 'none'
kaffeine: PostFilter: tvtime Apply integer value 0 on offset 8
kaffeine: PostFilter: Set parameter 'framerate_mode' to value 'half_top'
kaffeine: PostFilter: tvtime Apply integer value 1 on offset 12
kaffeine: PostFilter: Set parameter 'judder_correction' to value '0'
kaffeine: PostFilter: tvtime Apply integer value 0 on offset 16
kaffeine: PostFilter: tvtime Apply integer value 0 on offset 16
kaffeine: PostFilter: Set parameter 'use_progressive_frame_flag' to value '1'
kaffeine: PostFilter: tvtime Apply integer value 1 on offset 20
kaffeine: PostFilter: Set parameter 'chroma_filter' to value '0'
kaffeine: PostFilter: tvtime Apply integer value 0 on offset 24
kaffeine: PostFilter: Set parameter 'cheap_mode' to value '1'
kaffeine: PostFilter: tvtime Apply integer value 1 on offset 28
kaffeine: PostFilter: tvtime Apply integer value 1 on offset 28
kaffeine: KXineWidget: Deinterlace enabled: 1
kaffeine: PostFilter: Get output
kaffeine: PostFilter: Get input
kaffeine: KXineWidget: Playing: [http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl](http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl)
kaffeine: KXineWidget: Start event loop...
kaffeine: KXineWidget: xine event: progress info
kaffeine: KXineWidget: xine event: progress info
kaffeine: KXineWidget: Wait for valid length information
kaffeine: KXineWidget: Switch to audio channel -1
kaffeine: KaffeinePart: xine is playing
kaffeine: KXineWidget: xine event: progress info
kaffeine: Kaffeine: Set screensaver timeout to: 2 min
clehel@apagepe:~$ kaffeine: KXineWidget: xine event: playback finished
kaffeine: KaffeinePart::closeURL()
kaffeine: KXineWidget: Playing: /usr/share/apps/kaffeine/logo
[mpeg4 @ 0xb5b3a998]frame skip 8
[mpeg4 @ 0xb5b3a998]frame skip 8
kaffeine: KXineWidget: New video frame size: 654x360 - aspect ratio: 1.02222
kaffeine: KXineWidget: Switch to audio channel -1
kaffeine: KXineWidget: New video frame size: 654x360 - aspect ratio: 1.02222
kaffeine: KXineWidget: xine event: playback finished
kaffeine: KaffeinePart::slotPlay()
kaffeine: KXineWidget: Playing: [http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl](http://www.godsdirectcontact.eu.com/eng/multimedia/videos/HUN/LAN/1999hun01.wpl)
kaffeine: KXineWidget: xine event: progress info
kaffeine: KXineWidget: xine event: progress info
kaffeine: KXineWidget: Wait for valid length information
kaffeine: KXineWidget: Switch to audio channel -1
kaffeine: KaffeinePart: xine is playing
kaffeine: KXineWidget: New video frame size: 654x360 - aspect ratio: 1.02222
kaffeine: KXineWidget: xine event: progress info
kaffeine: KXineWidget: xine event: playback finished
kaffeine: KaffeinePart::closeURL()
kaffeine: KXineWidget: Playing: /usr/share/apps/kaffeine/logo
[mpeg4 @ 0xb5b3a998]frame skip 8
[mpeg4 @ 0xb5b3a998]frame skip 8
kaffeine: KXineWidget: Switch to audio channel -1
kaffeine: KXineWidget: New video frame size: 654x360 - aspect ratio: 1.02222
kaffeine: KXineWidget: xine event: playback finished
kaffeine: Kaffeine: Fake keypress event
kaffeine: Kaffeine: Fake keypress event

---

### Post by JLTB on 2005-08-22
From the looks of it Kaffeine thinks that the movie played correctly.  I'm no whiz with media stuff but I personally use VLC to play all my media content since it seems to work better than all the rest

'sudo apt-get install vlc' if you want to give it a shot.

PS: I don't know what a wpl file is, but maybe you don't have the correct codec to play it?  Try installing the w32codecs pack, etc to get more codecs.

---

### Post by clehel on 2005-08-23
Thank you. I installed vlc, it is a great player! Someone else suggested gmplayer, so I tried both. With vlc I ran into a codec problem, with mplayer I did not (don't ask me, why), but into another one. Anyway, with gmplayer now I manage to view streaming video, although not really in the way it is supposed to. I will make a separate post about it in another forum. Thanks again! O:)

---

### Post by cosine7 on 2006-11-21
> **clehel said:**
> Thank you. I installed vlc, it is a great player! Someone else suggested gmplayer, so I tried both. With vlc I ran into a codec problem, with mplayer I did not (don't ask me, why), but into another one. Anyway, with gmplayer now I manage to view streaming video, although not really in the way it is supposed to. I will make a separate post about it in another forum. Thanks again! O:)

gmplayer worked for me thanks!

---

