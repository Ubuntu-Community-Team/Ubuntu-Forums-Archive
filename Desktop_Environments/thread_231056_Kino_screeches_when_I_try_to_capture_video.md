---
title: "Kino screeches when I try to capture video"
date: 2006-08-06
forum: Desktop Environments
---

### Post by greenstar on 2006-08-06
I open up Kino switch to the capture tab and start a capture. As soon as the camera comes on and the capture actually starts recording, this hideous high-pitched scrreeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee sound comes out of my speakers & Kino freezes. I have to xkill Kino, or wait for the little dialog (after clicking the close button) that says something about Kino is blah blah blah, do you want to ?kill? it. Anyway, something like that and then it closes.

I ran Kino from terminal and here's the output, or what I could get... there were so many lines that I couldn't see/copy it all.

```

>>> Image Transition: Differences
>> audio filter repository created
>>> Audio Filter: No Change
>>> Audio Filter: Silence
>>> Audio Filter: Fade In
>>> Audio Filter: Fade Out
>> audio transition repository created
>>> Audio Transition: No Change
>>> Audio Transition: Cross Fade
>>> Audio Transition: Dub
>>> Audio Transition: Mix
> Creating Magick Page
>> Searching /usr/lib/kino-gtk2 for plugins
>>> Registering plugin /usr/lib/kino-gtk2/libdvtitler.so
>>> Registering plugin /usr/lib/kino-gtk2/libtimfx.so
>>> Registering plugin /usr/lib/kino-gtk2/libkinoplus.so
>>> Image Filter: Titler
>>> Image Filter: Superimpose
>>> Image Filter: Blur
>>> Image Filter: Color Hold
>>> Image Filter: Soft Focus
>>> Image Transition: Luma Wipe

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
>>> Image Create: FFMPEG Import

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed
>>> Image Create: Multiple Image Import
>>> Image Filter: Jerk

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
>>> Image Filter: ImageMagick Titler

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
>>> Image Filter: ImageMagick Overlay
>>> Image Filter: Pixelate
>>> Image Filter: Charcoal
>>> Image Filter: Pan and Zoom
>>> Image Filter: Colour Average
>>> Image Filter: Gamma
>>> Image Filter: Effect TV
>>> Image Filter: Pipe Filter
>>> Image Transition: Chroma key on blue

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
>>> Image Transition: Tweenies

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:9832): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed
>>> Audio Filter: FFMPEG Dub
> setting video preview size to 360x202
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
>>> AVC enabled
>> Constructing File Capture tracker
>> AV/C Disabled
>>> Trying /home/brandon/capture001.mov
>>> Trying /home/brandon/capture002.mov
>>> Trying /home/brandon/capture003.mov
>>>> Registering /home/brandon/capture003.mov with the tracker
stsd_init_audio: 16
>> Trying XVideo at 720x480
>>> XvQueryAdaptors count: 1
>>> Xv: ATI Radeon Video Overlay: ports 59 - 59
>>> formats supported: 4
>>>     0x32595559 (YUY2) packed
>>>     0x59565955 (UYVY) packed
>>>     0x32315659 (YV12) planar
>>>     0x30323449 (I420) planar
>>> 0: XV_IMAGE, 2048x2048 rate = 1/1
reader < # inFrames: 23, # outFrames: 25
reader < # inFrames: 22, # outFrames: 26
reader < # inFrames: 21, # outFrames: 27
reader < # inFrames: 20, # outFrames: 28
reader < # inFrames: 19, # outFrames: 29
reader < # inFrames: 18, # outFrames: 30
reader < # inFrames: 17, # outFrames: 31
reader < # inFrames: 16, # outFrames: 32
reader < # inFrames: 15, # outFrames: 33
reader < # inFrames: 14, # outFrames: 34
reader < # inFrames: 13, # outFrames: 35
reader < # inFrames: 12, # outFrames: 36
reader < # inFrames: 11, # outFrames: 37
reader < # inFrames: 10, # outFrames: 38
reader < # inFrames: 9, # outFrames: 39
reader < # inFrames: 8, # outFrames: 40
reader < # inFrames: 7, # outFrames: 41
reader < # inFrames: 6, # outFrames: 42
reader < # inFrames: 5, # outFrames: 43
reader < # inFrames: 4, # outFrames: 44
reader < # inFrames: 3, # outFrames: 45
reader < # inFrames: 2, # outFrames: 46
reader < # inFrames: 1, # outFrames: 47
reader < # inFrames: 0, # outFrames: 48
reader < # dropped frames: 1
reader < # dropped frames: 2
reader < # dropped frames: 3
reader < # dropped frames: 4
reader < # dropped frames: 5
reader < # dropped frames: 6
reader < # dropped frames: 7
reader < # dropped frames: 8
reader < # dropped frames: 9
reader < # dropped frames: 10
reader < # dropped frames: 11
reader < # dropped frames: 12
reader < # dropped frames: 13
reader < # dropped frames: 14
reader < # dropped frames: 15
reader < # dropped frames: 16
reader < # dropped frames: 17
reader < # dropped frames: 18
reader < # dropped frames: 19
reader < # dropped frames: 20
reader < # dropped frames: 21
reader < # dropped frames: 22
reader < # dropped frames: 23
reader < # dropped frames: 24
reader < # dropped frames: 25
reader < # dropped frames: 26
reader < # dropped frames: 27
reader < # dropped frames: 28
reader < # dropped frames: 29
reader < # dropped frames: 30
reader < # dropped frames: 31
reader < # dropped frames: 32
reader < # dropped frames: 33
reader < # dropped frames: 34
reader < # dropped frames: 35
reader < # dropped frames: 36
reader < # dropped frames: 37
reader < # dropped frames: 38
reader < # dropped frames: 39
reader < # dropped frames: 40
reader < # dropped frames: 41
reader < # dropped frames: 42
reader < # dropped frames: 43
reader < # dropped frames: 44
reader < # dropped frames: 45
reader < # dropped frames: 46
reader < # dropped frames: 47
reader < # dropped frames: 48
reader < # dropped frames: 49
reader < # dropped frames: 50
reader < # dropped frames: 51
reader < # dropped frames: 52
reader < # dropped frames: 53
reader < # dropped frames: 54
reader < # dropped frames: 55
reader < # dropped frames: 56
reader < # dropped frames: 57
reader < # dropped frames: 58
reader < # dropped frames: 59
reader < # dropped frames: 60
reader < # dropped frames: 61
reader < # dropped frames: 62
reader < # dropped frames: 63
reader < # dropped frames: 64
reader < # dropped frames: 65
reader < # dropped frames: 66
reader < # dropped frames: 67
reader < # dropped frames: 68
reader < # dropped frames: 69
reader < # dropped frames: 70
reader < # dropped frames: 71
reader < # dropped frames: 72
reader < # dropped frames: 73
reader < # dropped frames: 74
reader < # dropped frames: 75
reader < # dropped frames: 76
reader < # dropped frames: 77
reader < # dropped frames: 78
reader < # dropped frames: 79
reader < # dropped frames: 80
reader < # dropped frames: 81
reader < # dropped frames: 82
reader < # dropped frames: 83
reader < # dropped frames: 84
reader < # dropped frames: 85
reader < # dropped frames: 86
reader < # dropped frames: 87
reader < # dropped frames: 88
reader < # dropped frames: 89
reader < # dropped frames: 90
reader < # dropped frames: 91
reader < # dropped frames: 92
reader < # dropped frames: 93
reader < # dropped frames: 94
reader < # dropped frames: 95
reader < # dropped frames: 96
reader < # dropped frames: 97
reader < # dropped frames: 98
reader < # dropped frames: 99
>> Kino Common newFile
>> Leaving Capture
>>> using audio from separarate Quicktime audio track
>>> Received playlist to store at position 1
>>>> Adding to end
>>> Received playlist to store at position 2
>>>> Adding to end
>> AV/C Enabled
reader < # dropped frames: 100
reader < # dropped frames: 101
reader < # dropped frames: 102
reader < # dropped frames: 103
reader < # dropped frames: 104
reader < # dropped frames: 105
reader < # dropped frames: 106
reader < # dropped frames: 107
reader < # dropped frames: 108
reader < # dropped frames: 109
reader < # dropped frames: 110
reader < # dropped frames: 111
reader < # dropped frames: 112
reader < # dropped frames: 113
reader < # dropped frames: 114
reader < # dropped frames: 115
reader < # dropped frames: 116
reader < # dropped frames: 117
reader < # dropped frames: 118
reader < # dropped frames: 119
reader < # dropped frames: 120
reader < # dropped frames: 121
Killed

``` 
I've searched the forums and haven't found anything about this. 

If anyone has any ideas, I'd appreciate the help.

Also, I can't get Kino to open when I plug in & turn on my Videocamera. I put "kino" in the Digital Video Camera section of the Cameras tab. Most of the other apps in the other sections & tabs have some stuff like %m %f and some other $*!7 like that, though I haven't a clue what they mean. I managed to figure out a while back that I had to have the %m after vlc so inserting a DVD would not only open vlc, but actually start playing the movie too.:rolleyes: Just having vlc there opened vlc, but didn't load or play the movie. So now I want to make Kino open when my Videocamera is detected. Can anyone help?

Greenstar

---

### Post by rafalr on 2006-08-14
Hi, 

I encountered something very similar, plus:
- when starting Kino as user, it can not see the camera (if started in terminal as gksudo kino it can see the camera)
- when trying some tests of exporting, there are no tools available in DV Pipe sub-menus
- when captuting, the actual image is garbled as in the screenshot (is that matter of codecs ?).

If it matters, I recently played with installinmg XGL and compriz, however was launching Kino in plain gnome-session.

Pls let me know if you figured it out.
Rafal

---

### Post by greenstar on 2006-08-15
> **rafalr said:**
> 
- when starting Kino as user, it can not see the camera (if started in terminal as gksudo kino it can see the camera)
- when trying some tests of exporting, there are no tools available in DV Pipe sub-menus
- when captuting, the actual image is garbled as in the screenshot (is that matter of codecs ?).


I have not experienced any of the additional symptoms you describe, so I'm afraid I won't be much help. 

[rant]
I've been looking today on the Kino forums, and all I've seen is advice saying that my version must be wrong or some dependency was compiled against the wrong version of something else or the wrong kernel... blah, blah, blah. I don't think we're gonna get this fixed anytime soon. It will likely be some months to a year or more before Kino is fixed properly. Anyway, I'll be moving on with my life and I suppose I'll use dvgrab for capture and whatever else I can find to edit my stuff. Ugggh, I hate even looking at cinelerra, it's such an eyesore. I'd actually rather look at text-mode in a terminal than the cinelerra GUI. Cinelerra's not even remotely easy to use & I hate it with a humongous passion. [/rant]

Greenstar

---

### Post by rafalr on 2006-08-25
Hi,

I solved all my problems/sympotms in 10 secs: I figured out they are all related to XGL working on my machine. All I needed to do was:
- to hash all changes I did in /etc/gdm/gdm.conf-custom while configuring XGL and 
- not start compiz.

However if you do not run XGL it would not help you ...
Rafal

---

### Post by rafalr on 2006-08-25
Hi,

I solved all my problems/sympotms in 10 secs: I figured out they are all related to XGL working on my machine. All I needed to do was:
- to hash all changes I did in /etc/gdm/gdm.conf-custom while configuring XGL and 
- not start compiz.

However if you do not run XGL it would not help you ...
Rafal

---

### Post by greenstar on 2006-08-27
No XGL/Compiz here. In my opinion, XGL/Compiz is garbageware. It's nothing more than eyecandy at the expense of the ruining an otherwise perfectly good Ubuntu installation.

I stay away from that kind of garbage. Using trashware like that is just begging for system instability & software conflicts & problems. If I wanted an unstable system, I'd go back to that *other* mainstream OS.

Greenstar

---

