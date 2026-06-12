---
title: "Kaffeine Crash"
date: 2005-06-04
forum: Desktop Environments
---

### Post by Gtaylor on 2005-06-04
Recently I've been having an issue with Kaffeine. It plays the videos just fine but when I close the player, it crashes. This isn't a big deal but the KCrash dialog pops up every time and this gets to be a nuisance. Running Kaffeine in a terminal I get the following output:

```
gtaylor@stimpy:~ $ kaffeine: PlayList: add 1 items to playlist
kaffeine: PlayList: Check for subtitle files
kaffeine: KaffeinePart::openURL(): /home/gtaylor/Desktop/leeroy.wmv
kaffeine: KaffeinePart: Got single track
kaffeine: KaffeinePart::slotPlay()
kaffeine: KXineWidget: Display aspect ratio (v/h): 0.976401
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
kaffeine: Set volume to: 62
kaffeine: KXineWidget: New visualization plugin: none
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
kaffeine: KXineWidget: Playing: /home/gtaylor/Desktop/leeroy.wmv
kaffeine: KXineWidget: Start event loop...
External func OLEAUT32.dll:8
Creating new registry
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
kaffeine: KXineWidget: xine event: channels changed
GetOutput r=0x0   size:921600  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU   &#9618;
Decoder is capable of YUV output (flags 0x1b)
kaffeine: KXineWidget: New video frame size: 655x480 - aspect ratio: 1
kaffeine: KXineWidget: Switch to audio channel -1
kaffeine: KaffeinePart: xine is playing
kaffeine: KaffeinePart: got new frame size from xine
kaffeine: Kaffeine: new video frame size: 640x480
kaffeine: KXineWidget: New video frame size: 655x480 - aspect ratio: 1
kaffeine: KaffeinePart: got new frame size from xine
kaffeine: Kaffeine: new video frame size: 655x480
kaffeine: Kaffeine: destructor
kaffeine: PostFilter: Get output
kaffeine: PostFilter: Get input
kaffeine: KXineWidget: Exiting event loop...
kaffeine: KXineWidget: Shut down xine engine
kaffeine: KXineWidget: Unwire video filters
kaffeine: PostFilter: Delete Postprocessing Filter: tvtime
kaffeine: KXineWidget: Dispose event queue
kaffeine: KXineWidget: Dispose stream
Total Unfree 60 bytes cnt 1 [(nil),0]
kaffeine: KXineWidget: Close audio driver
kaffeine: KXineWidget: Close video driver
kaffeine: KXineWidget: Set CD/VCD/DVD path back
kaffeine: KXineWidget: Save xine config to: /home/gtaylor/.kde/share/apps/kaffeine/xine-config
kaffeine: KXineWidget: Close xine engine
kaffeine: KXineWidget: Close xine display
kaffeine: KXineWidget: xine closed
kaffeine: KaffeinePart: destructor
kaffeine: KaffeinePart: save config
KCrash: Application 'kaffeine' crashing...
``` 

Any ideas?

---

### Post by Jonathan2007 on 2005-06-04
Do you have the "fix" package? Search for it on the forums. It worked like a charm for me. Everyone's Kaffeine was crashing a ton and the package fixed it for everyone.

---

### Post by Gtaylor on 2005-06-05
That did the trick, thanks.

---

