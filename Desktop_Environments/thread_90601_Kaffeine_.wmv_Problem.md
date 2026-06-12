---
title: "Kaffeine .wmv Problem"
date: 2005-11-15
forum: Desktop Environments
---

### Post by DoeRayMe on 2005-11-15
Im having a slight problem with Kaffeine, it plays everything else, even other .wmv files. but with this one i get this message

> The source seems encrypted, and can't be read. (Media stream scrambled/encrypted)

Thats with the xine engine, how can i make this play?

---

### Post by manubreizh on 2005-11-15
hi,
do you have w32codec package installed ?
it should solve the problem if not post more, we'll try to fix it

---

### Post by DoeRayMe on 2005-11-15
yeah its installed, can play other wmv movies easy but its just this one

---

### Post by manubreizh on 2005-11-15
is it something dealing with Data Rights Managements ? did you ever achieve in watching it once or is it an error you have even the first time you tried ?
i can't see others reasons to explain your problem, maybee with more informations or someone more efficient in the forum

---

### Post by DoeRayMe on 2005-11-15
its a *little movie* file i downloaded

---

### Post by PokerFacePenguin on 2005-11-15
[QUOTE=manubreizh]hi,
do you have w32codec package installed ?
it should solve the problem if not post more, we'll try to fix it[/QUOTE]


where do i get this package?  doesnt show up in adept........

my sources.list is as follows.........

> ## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restric                                            ted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


---

### Post by PokerFacePenguin on 2005-11-15
answered my own question with a search......oops

---

### Post by daller on 2005-12-18
Solved the problem???

- I have the problem on 10 files for now...

---

### Post by daller on 2005-12-18
If it's any help, here's some output:

```


DVB 0 : Ingen sådan fil eller filkatalog
DVB 1 : Ingen sådan fil eller filkatalog
DVB 2 : Ingen sådan fil eller filkatalog
DVB 3 : Ingen sådan fil eller filkatalog
kaffeine: No DVB device found.
kaffeine: Window manager: KWin found
kaffeine: Kaffeine:: Try to load service: kaffeine_part
kaffeine: This is a KMediaPart...
kaffeine: KaffeinePart: Creating new KaffeinePart...
kaffeine: KaffeinePart: Using xine-config file: /home/daniel/.kde/share/apps/kaffeine/xine-config
kaffeine: PlayList: add 1 items to playlist
kaffeine: PlayList: Check for kaffeine/noatun/m3u/pls/asx playlist
kaffeine: PlayList: Try loading kaffeine playlist
kaffeine: PlaylistImport: kaffeine: /home/daniel/.kde/share/apps/kaffeine/playlists/NY.kaffeine
kaffeine: PlayList: add 1 items to playlist
kaffeine: PlayList: Check for subtitle files
kaffeine: KaffeinePart::openURL(): /home/daniel/top/codec/1.wmv
kaffeine: KaffeinePart: Got single track
kaffeine: KaffeinePart::slotPlay()
kaffeine: KXineWidget: Display aspect ratio (v/h): 0.975764
kaffeine: KXineWidget: Using xine version 1.0.1
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
kaffeine: Set volume to: 70
kaffeine: KXineWidget: Start event loop...
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
kaffeine: KXineWidget: Playing: /home/daniel/top/codec/1.wmv
kaffeine: KXineWidget: xine event: xine message
kaffeine: KXineWidget: xine event: channels changed
kaffeine: KXineWidget: xine event: channels changed
External func OLEAUT32.dll:8
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU   &#9618;
Decoder is capable of YUV output (flags 0x1b)
kaffeine: KXineWidget: xine event: playback finished
kaffeine: KXineWidget: Switch to audio channel -1
kaffeine: KaffeinePart: xine is playing
kaffeine: Kaffeine: Set screensaver timeout to: 2 min
daniel@ubuntu:~/top/codec$ kaffeine: KaffeinePart::closeURL()
kaffeine: KXineWidget: Playing:
kaffeine: ERROR: KXineWidget: Can't find/play logo file!


```

---

