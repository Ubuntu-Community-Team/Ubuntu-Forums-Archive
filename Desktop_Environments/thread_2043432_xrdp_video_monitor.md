---
title: "xrdp video monitor"
date: 2012-08-16
forum: Desktop Environments
---

### Post by allen47401 on 2012-08-16
[FONT=Courier New][SIZE=3][FONT=Calibri]I’m running xrdp on an Ubuntu 12.04 LTS (Desktop) machine and administering it remotely with a Windows 7 machine. The Linux machine is setup headless in my entertainment center as a media and file server. Well, almost headless. Its HDMI output is connected to my TV. Its sound is connected to an amplifier and speakers, which plays audio files, both local and web based nicely. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Now that those things were working, the next step was to set it up to play video files and send them out to the TV. That’s where I’m stuck. I haven’t found a way to make it play video on the Linux monitor (my TV) when accessing Linux remotely using xrdp from my Windows machine. Instead, all video plays on my Windows machine.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]If I connect a keyboard and mouse up to the Linux box and play a video from there, it, of course, works fine, but that defeats my purpose.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]You may be wondering why I installed the Ubuntu Desktop version instead of the Server version. Well, I did at first, but I couldn’t get the server version to enable sound, Blue Tooth or the DVD, at least running headless.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Is xrdp just too simplistic to allow me to do redirect the Linux video output? Or is there some other way to redirect video from my Windows machine back to the Linux machine? It seems ironic I have just the opposite situation with sound. I can’t force Linux to redirect sound away from it to my Windows machine. Not a big deal, since I want sound to play on the Linux box anyway.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Thanks for any suggestions[/FONT][/SIZE]
[/FONT]

---

### Post by SteveDee on 2012-08-17
> **allen47401 said:**
> [FONT=Courier New][SIZE=3][FONT=Calibri]...Is xrdp just too simplistic to allow me to do redirect the Linux video output?...

Just reading this over breakfast so my answer may not be 100%, but I think what you are doing with RDP is creating a new user session. What you need to do is view an existing session.

With VNC you can specify the remote screen number. You can do your own search on this, and here is an old post where I touched on this in post#7: [http://ubuntuforums.org/showthread.php?t=1013366&highlight=video](http://ubuntuforums.org/showthread.php?t=1013366&highlight=video) 

Sorry this is a rushed answer, but I hope this is of some use.

---

