---
title: "How does one do this?"
date: 2006-01-02
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-02
I have seen some mpeg/mpg demos that people made showing their desktop as it's actually in use. These demos are in .mpeg/.mpg format and show the cursor moving, files being opened, websites being opened, etc. How do I make these "movies" in .mpeg/.mpg format to show a demo of something on my desktop? Which app(s) do I need to install for this?

---

### Post by encompass on 2006-01-03
vnc2swf does something like that... pm me and when I am back on my linux box at home... I will tell you the one I have istalled... can't remember for the life of me...

---

### Post by encompass on 2006-01-04
here it is.... desktop session recorder.  Tell me whay you think of it.

---

### Post by 23meg on 2006-01-04
There's istanbul, the desktop session recorder. It's in the repositories.

---

### Post by ardchoille on 2006-01-04
Thanks guys, I'll check it out :)

---

### Post by ardchoille on 2006-01-05
istanbul records to .ogg format. I need something to record in .mpeg or .mpg format, so istanbul won't work for me.

---

### Post by cutOff on 2006-01-10
[QUOTE=ardchoille]istanbul records to .ogg format. I need something to record in .mpeg or .mpg format, so istanbul won't work for me.[/QUOTE]
You can use mencoder to convert ogg to mpg:

$ mencoder video.ogg -o video.mpg -ovc divx4

---

### Post by ardchoille on 2006-01-10
[QUOTE=cutOff]You can use mencoder to convert ogg to mpg:

$ mencoder video.ogg -o video.mpg -ovc divx4[/QUOTE]
Ah hah! Thank you for this info.

---

### Post by az on 2006-01-10
[QUOTE=23meg]There's istanbul, the desktop session recorder. It's in the repositories.[/QUOTE]
Does it work for you?

It only spews out garbage for me.

---

### Post by mlalkaka on 2006-01-10
Another program is xvidcap ([http://xvidcap.sourceforge.net)](http://xvidcap.sourceforge.net)). I haven't tried it yet, but it does record to MPEG format and I believe it can also record sound.

---

### Post by cutOff on 2006-01-10
[QUOTE=azz]Does it work for you?

It only spews out garbage for me.[/QUOTE]
What's the problem? normally it saves the video in home dir.

A good place to know how it works 
[http://fedoraproject.org/wiki/ScreenCasting](http://fedoraproject.org/wiki/ScreenCasting)

---

### Post by az on 2006-01-10
[QUOTE=cutOff]What's the problem? normally it saves the video in home dir.

A good place to know how it works 
[http://fedoraproject.org/wiki/ScreenCasting](http://fedoraproject.org/wiki/ScreenCasting)[/QUOTE]
That seems very helpful.  Especially:

"Recommended Settings
Set your Xorg server display to use 800x600. You can't just set this resolution via gnome's support for xrandr yet. To make sure you get a proper screen capture you need to make sure that the X server itself is set to 800x600 (with system-config-display for instance) and that the gnome desktop is configured to use the default X resolution and refresh rate. If you attempt to lower your desktop resolution using xrandr for your desktop you will most likely see artifacts in the videos. 

Set istanbul framerate to 1.0 frames per second. This should be fast enough to record most human interactions with the desktop and will be slow enough to prevent egregious problems with frames being dropped. Upstream is currently working on fixing the performance issues with capturing the x display image. The recommended framerate will be adjusted as performance improvements to gstreamer's display capture plugin are made available. 

Set the istanbul encode image size to be 240x192 for a web friendly video size. This is 1/4 the area of the desktop and text should still be legible. If you shrink the image too much as part of the encoding process small text can become obscured. "


I will try this later today.  My problem was a choppy, artifactual ogg.theora output.  I was running at the default (12 fps?) at 1024x768.

---

