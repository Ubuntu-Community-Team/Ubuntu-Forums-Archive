---
title: "Screen Capturing"
date: 2014-01-17
forum: Desktop Environments
---

### Post by nanisahu on 2014-01-17
Hi This is Nanaji Sahukara,

I'm new for Linux X Display. How to Capture the X window(Screen Grabing) and play in another X Window. I've tried in OpenCV, In OpenCV it can capture only webcam devices only. But i need screen capture. Please any one help me...

Thanks in advanced
Nanaji Sahukara

---

### Post by TheFu on 2014-01-17
ffmpeg can record a screen. [http://www.commandlinefu.com/commands/view/148/capture-video-of-a-linux-desktop](http://www.commandlinefu.com/commands/view/148/capture-video-of-a-linux-desktop)

However, if you just want to use a remote display, X/Windows will do that easily. It is built in using just the DISPLAY environment variable.  If you use 'ssh -X {userid}@{other-UNIX/Linux-host} cmd-on-remote-host' will do it easily assuming the machine you are on is running an X-Server.

But I could be misunderstanding the question.

---

