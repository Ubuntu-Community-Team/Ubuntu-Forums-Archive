---
title: "get x,y offset,width,height of area on desktop to record via recordmydesktop"
date: 2021-10-01
forum: Desktop Environments
---

### Post by buzlite on 2021-10-01
I'm would like to use recordmydesktop app (this is CLI app). This app allow me to specify a location of an area on the desktop to record.
Hence, I'm looking for a program that allows me to draw a square on the desktop and it would show me the x y offset as well as the width and height of such a square. I could then use this data to configure the recordmydesktop app via CLI
Does such a utility exist?

I'm using xubuntu based on ubuntu 20.04.3

---

### Post by TheFu on 2021-10-01
If you use X11, not Wayland, you can use
```
$ xwininfo -stats
```
then click in the window to get the geometry.

for example:
```
$ xwininfo -stats

xwininfo: Please select the window about which you
          would like information by clicking the
          mouse in that window.

xwininfo: Window id: 0x2c0000f "ssh"

  [B]Absolute upper-left X:  7
  Absolute upper-left Y:  718[/B]
  Relative upper-left X:  0
  Relative upper-left Y:  0
[B]  Width: 739
  Height: 403[/B]
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +7+718  -1174+718  -1174-79  +7-79
  -geometry 72x21+1-73
```

Most X11 programs can be specifically placed using the -geometry option.  So, 
```
$ xterm -geometry 72x21+1-73 
```
places any exactly sized xterm in that location on the current workspace.  

Be careful with non-terminals for sizes.  I pointed it at a firefox instance and it returned:
-geometry 1783x1000-9-30 .... which has to be pixels for all the open tabs.  I didn't do any research, but the "Corners" output seems more useful.
Corners:  +122+164  -15+164  -15-36  +122-36 for GUI stuff.

Anyway, that's a starting point for your testing/research.

---

### Post by T6&amp;sfpER35% on 2021-10-01
why go to all that trouble ,when **simplescreenrecorder **&#8203;can do all that with a few clicks

---

### Post by TheFu on 2021-10-01
> **3nd said:**
> why go to all that trouble ,when **simplescreenrecorder **&#8203;can do all that with a few clicks

Automation.

I use SSR too, btw.

---

### Post by buzlite on 2021-10-06
Thanks for the simplescreenrecorder app. That'll be useful.
Is there a stand alone app that allows me to outline a random square on desktop and have the xy offset, height, width info?

---

### Post by TheFu on 2021-10-06
> **buzlite said:**
> Thanks for the simplescreenrecorder app. That'll be useful.
Is there a stand alone app that allows me to outline a random square on desktop and have the xy offset, height, width info?

ffmpeg can capture any X11 screen or portion of the screen easily.  No clue if Wayland is supported, but usually only one or the other works.  I don't know of **any** tool that can deal with both X11 and Wayland.  Google will find 50 examples of ffmpeg screen captures easily. 
[https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop) is one. It would probably be easiest to specify the window geometry at program start, then tell ffmpeg to capture that exact area.

I use SimpleScreenRecorder a few times a month. Sometimes it is the easiest way to capture a stream and audio from 2 different sources.  

For example, American football games.  I have a broadcast TV tuner on the network, but prefer the college radio station play-by-play team over the TV guys.  Rather than recording both, then muxing them together later ... the radio station is 6-60 seconds behind the TV ... so inserting a delay into the video is necessary.  I don't want to be 2 hrs behind, but 5 minutes behind is 100% fine.  PVRs are great.

---

### Post by &amp;KyT$0P# on 2021-10-08
> **buzlite said:**
> Is there a stand alone app that allows me to outline a random square on desktop and have the xy offset, height, width info?

slop.  It's available in standard Ubuntu repositories -
```
sudo apt-get install slop
```

---

