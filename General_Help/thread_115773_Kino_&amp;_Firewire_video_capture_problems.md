---
title: "Kino &amp; Firewire video capture problems"
date: 2006-01-11
forum: General Help
---

### Post by spetko on 2006-01-11
I have a problem with Kino and video capturing. If I start to capture video, Kino crashes within a few seconds. I browsed around the forums but couldn't find anything useful. I'm not sure if it is Kino or firewire problem, but I get the video on Kino, however it seems it is droping a lot of frames. Kino crashes with the following listing:
(kino:9872): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed
>>> Audio Filter: FFMPEG Dub
>> Starting Editor
>> Kino Common newFile
>> Creating undo/redo buffer
>>> Received playlist to store at position 0
>>>> Adding to end
>> on_main_window_map_event
>> Leaving Editor
>> Left Editor
>> Starting Capture
>> AV/C Enabled
>>> Using raw1394 capture
reader < # incomplete dropped frames: 1
reader < # incomplete dropped frames: 2
>> Trying XVideo at 720x576
>>> XvQueryAdaptors count: 0
>> Destroying XV Displayer
>> Trying XVideo at 360x288
>>> XvQueryAdaptors count: 0
>> Destroying XV Displayer
reader < # incomplete dropped frames: 3
reader < # incomplete dropped frames: 4
reader < # incomplete dropped frames: 5
reader < # incomplete dropped frames: 6
reader < # incomplete dropped frames: 7
reader < # incomplete dropped frames: 8
reader < # incomplete dropped frames: 9
reader < # incomplete dropped frames: 10
reader < # incomplete dropped frames: 11
reader < # incomplete dropped frames: 12
reader < # incomplete dropped frames: 13
reader < # incomplete dropped frames: 14
reader < # incomplete dropped frames: 15
reader < # incomplete dropped frames: 16
reader < # incomplete dropped frames: 17
reader < # incomplete dropped frames: 18
reader < # incomplete dropped frames: 19
reader < # incomplete dropped frames: 20
reader < # incomplete dropped frames: 21
reader < # incomplete dropped frames: 22
reader < # incomplete dropped frames: 23
reader < # incomplete dropped frames: 24
reader < # incomplete dropped frames: 25
reader < # incomplete dropped frames: 26
reader < # incomplete dropped frames: 27
reader < # incomplete dropped frames: 28
reader < # incomplete dropped frames: 29
reader < # incomplete dropped frames: 30
reader < # incomplete dropped frames: 31
reader < # incomplete dropped frames: 32
>>> AVC enabled
AVC Status: Unknown state
reader < # incomplete dropped frames: 33
reader < # incomplete dropped frames: 34
reader < # incomplete dropped frames: 35
reader < # incomplete dropped frames: 36
reader < # incomplete dropped frames: 37
reader < # incomplete dropped frames: 38
reader < # incomplete dropped frames: 39
reader < # incomplete dropped frames: 40
>>> AVC status error
reader < # incomplete dropped frames: 41
reader < # incomplete dropped frames: 42
reader < # incomplete dropped frames: 43
reader < # incomplete dropped frames: 44
reader < # incomplete dropped frames: 45
>> Constructing File Capture tracker
>>> AVC status error
reader < # incomplete dropped frames: 46
reader < # incomplete dropped frames: 47
reader < # incomplete dropped frames: 48
reader < # incomplete dropped frames: 49
reader < # incomplete dropped frames: 50

Kino experienced a segmentation fault.
Dumping stack from the offending thread

Obtained 6 stack frames.
kino(__gxx_personality_v0+0x33e) [0x80740f2]
[0xffffe420]
/usr/lib/libraw1394.so.5(raw1394_loop_iterate+0x1b5) [0xb7683325]
kino(_ZN13raw1394Reader6ThreadEv+0x9c) [0x80b07f8]
/lib/tls/i686/cmov/libpthread.so.0 [0xb7694361]
/lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb74e7bde]

Done dumping - exiting.


*******************
I have no idea where to go from now. Any ideas?

---

