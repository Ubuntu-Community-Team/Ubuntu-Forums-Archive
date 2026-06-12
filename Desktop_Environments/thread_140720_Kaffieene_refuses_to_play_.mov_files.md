---
title: "Kaffieene refuses to play .mov files"
date: 2006-03-06
forum: Desktop Environments
---

### Post by Valhalla on 2006-03-06
Kaffeine is refusing to play any quicktime files on my computer, or on the web, such as the ones from Apple trailers.  I have installed the w32codecs package, and mplayer seems to work correctly.  It is my understanding that mplayer relies on the w32codecs package as well for playback support, so I don't understand what is wrong.  I have tried with both the xine engine and the gstreamer engine, and I have gstreamer-pitfdll installed anf followed the readme to register the plugins with gstreamer.  Any assistance would be appreciated, since this is very frustrating.

---

### Post by hod139 on 2006-03-06
This is the problem with closed formats.  Until apple chooses to release a linux version of quicktime, you will run into these kinds of issues.  The open source drivers are ok, but they will fail for many .mov files.

---

### Post by Valhalla on 2006-03-06
Well, I tried registering the plugins with gst again, and now I can get sound playback with the gstreamer backend.  However, I get an audio visualization.  Thats strikes me as wrong somehow [-( .

---

### Post by hod139 on 2006-03-06
I've had the same thing happen.  Audio but no video.  Very annoying.

---

