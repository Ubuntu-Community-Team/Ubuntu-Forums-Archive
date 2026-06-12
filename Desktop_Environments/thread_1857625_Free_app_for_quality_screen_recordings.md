---
title: "Free app for quality screen recordings?"
date: 2011-10-10
forum: Desktop Environments
---

### Post by sneakyimp on 2011-10-10
I'm interested in creating some tutorials in the form of videos.  Can anyone recommend a good (and ideally FREE) piece of software to record one's actions on an ubuntu machine? I'm running 11.04.  I'd like to be able to perform actions with applications and speak into a USB microphone to make the video.

Any suggestions are much appreciated.

---

### Post by dodo3773 on 2011-10-10
I have always used "gtk-recordmydesktop" (with the "Outline Capture Area On Screen" box unchecked). Some people prefer ffmpeg though.

---

### Post by sneakyimp on 2011-10-10
Thanks for the info.  I wasn't aware ffmpeg did video screen capture. I'm looking into these now.

---

### Post by FakeOutdoorsman on 2011-10-11
> **sneakyimp said:**
> Thanks for the info.  I wasn't aware ffmpeg did video screen capture. I'm looking into these now.
If you want to try using FFmpeg see [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

If you don't want to compile FFmpeg as shown in the guide you can change the example command in **Step 1** to:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```
You may have to enable the libx264 encoder if you decide to use the repository FFmpeg. See option B or C in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

