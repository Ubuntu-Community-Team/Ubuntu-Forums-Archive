---
title: "ffmpeg sources desktop webcam"
date: 2020-06-29
forum: Desktop Environments
---

### Post by affarone2 on 2020-06-29
Hello
I want my webcam (HP TrueVision HD Camera (0xxx: 0xxx) to record what I'm doing on the Desktop with ffmpeg. Which is the right way to do it?)

---

### Post by TheFu on 2020-07-01
I&#8217;m confused by the question.

A webcam should be used to record people, not the desktop.

To record the desktop, use a screen capture tool like SimpleScreenRecorder.  it is possible to use ffmpeg and capture the desktop and there are lots of example commands any web search will find for that, but the simplicity of SSR make it the tool i use for stuff like this.

if you want to have both on the same screen, then use a tool like OBS to capture the screeen and use the webcam as a video input to put your talking head in a corner.

if my answer doesn't make sense, perhaps you can try explaining again?

---

### Post by affarone2 on 2020-07-07
I am interested that my webcam projects the desktop when I am in a videochat or on skype. 
Manycam for windows does it.

[IMG]https://www.maketecheasier.com/assets/uploads/2011/01/manycam-desktop-sharing.png[/IMG]

---

### Post by TheFu on 2020-07-07
Video chat programs will share your desktop natively.  I use this almost daily.

Some can merge my "talking head" with either a specific application or my entire desktop during the video chat.  I use this almost daily too. No need for SSR or ffmpeg or anything else. It is built into the webrtc webpage.  I don't use skype, but it works fine in jitsi.

If you don't want to merge 2 video inputs into 1 output live to be streamed via any application, then only OBS is needed, but with a virtual v4l2 driver.  OBS can stream to a number of public video sharing websites live.  Vimeo, YT, etc.  Here's a project [https://github.com/floe/deepbacksub](https://github.com/floe/deepbacksub) for recognizing a person so chromakey isn't needed. The virtual **v4l2loopback** driver is what lets it work with any of the video tools you want. The github link has a link to that project.

---

### Post by affarone2 on 2020-07-10
v4l2loopback is fine for me. 
But does it also work with cheese or do I have to install guvcview?

---

### Post by TheFu on 2020-07-10
Just to be clear, you don't just want something like this:
```
ffmpeg -video_size 1024x768 -framerate 25 -f x11grab -i :0.0+100,200 -f pulse -ac 2 -i default output.mkv
```
Ref: [https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop)

If you do, **simplescreenrecorder** is the easiest way, but knock yourself out tweaking and using ffmpeg.

---

### Post by affarone2 on 2020-07-11
I'm also interested in ffmpeg but I know you can do the same thing with OBS v4l2loopback.
But other than that I have to install ffmpeg + v4l2loopback ?.
v4l2loopback. how do i install it?

---

### Post by TheFu on 2020-07-11
[LIST]
[*] I still don't have any clue what it is that you want.
[*] Have you attempted to use any of the suggestions already provided? How did they work?
[*] If you need to ask how to install a program/library that is already in the standard repositories, then a lack of background in Linux will be a huge limitation for anything slightly complex.  Start here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) to begin building the necessary background.
[/LIST]

---

### Post by affarone2 on 2020-07-11
I want to do the same thing as the youtube video but he doesn't explain how to do the steps.
[https://www.youtube.com/watch?v=Eca509IDLdM](https://www.youtube.com/watch?v=Eca509IDLdM)

---

