---
title: "remote desktop::REALLY slow"
date: 2007-03-02
forum: Desktop Environments
---

### Post by binary_dreamer on 2007-03-02
Hi i got a machine running edgy and i followed the guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_remote_desktop_.28not_secure.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_configure_remote_desktop_.28not_secure.29)
the problem is that the response is really slow. the thing is that i cannot find anywhere to change the settings for the vnc server to allow different type of compression and/or its level. 

NOTE:
when i reboot to windows and i setup the vnc server it works perfectly. it is really smooth.

---

### Post by binary_dreamer on 2007-03-03
fixed.

---

### Post by md81544 on 2007-04-20
"Fixed" is a pretty lame follow up.  What did you do to fix it?  It might be useful to others.

---

### Post by jzlharvey on 2007-08-07
I have been fighting this for a long time.  Can you tell me what you did to fix it?

---

### Post by callan79 on 2007-08-08
> **jzlharvey said:**
> I have been fighting this for a long time.  Can you tell me what you did to fix it?

Same thing - I've noticed big differences in VNC performance. I don't have a lot of experience VNC'ing IN TO my Feisty box, but using xtightvncviewer from Feisty to a remote Windows computer was significantly slower than windows to windows (still using VNC).

Would love to hear the solution!!

Cheers
Callan

---

### Post by SadaraX on 2007-10-15
I am having similar speed problems, except that I use xtightvncviewer (with tightvncserver) going Linux to Linux (Feisty to Feisty). It is SO SLOW! Does anyone know why?

When I connect to my Linux box from a windows machine, it is very fast.

---

### Post by process91 on 2008-03-27
Been having these problems to, thought I would chime in and offer some help if I can.

Check the server/client configurations.
From what I've read/tried, connecting from Linux to an UltraVNC server just won't work.

I was using RealVNC server with the 4.1 protocol and the standard xvncviewer. When I installed xvnc4viewer and connected my speed was comparable to the standard windows/windows connection.

Hardy will be coming with xtightvncviewer as default, and I wanted to find out why. So I installed it. When connecting with xtightvncviewer to the RealVNC server, I got terrible performance results. Not satisfied, I then decided to install TightVNC Server on the Windows machine. The speed was better, but I RealVNC was still faster. I noticed the windows server was using TightVNC 1.39 and Ubuntu Hardy has only packaged TightVNC 1.29. I still wasn't satisfied, so I got the TightVNC1.39  rpm and converted it to a deb package to try out matching versions. I compiled the results below.

RealVNC 4 Server & xvnc4viewer Client
Cold Start - 2s
Cold Start Graphics Intensive - 13s
Start Menu - 3s
Minimize Full-Screen Window - 3s
Maximize Window from Task Bar - 19s
Maximize/Restore Open Window - 2s

TightVNC 1.39 Server and xtightvncviewer Client
Cold Start - 3s
Cold Start Graphics Intensive - 17s
Start Menu - 3s
Minimize Full-Screen Window - 4s
Maximize Window from Task Bar - 16s
Maximize/Restore Open Window - 2s

As you can see, it's pretty much a wash. The HUGE feature benefit (imho) to RealVNC is that if you have to scroll the viewer (host desktop is larger than yours) or if you have to move other windows on top of the VNC window it doesn't have to re-draw anything. (period) TightVNC does.

***Simple Instructions***
**For RealVNC**
Install: ```
sudo apt-get install xvnc4viewer
```Run: ```
xvnc4viewer example.server.com:5901
```**For TightVNC**
Install: ```
sudo apt-get install xtightvncviewer
```Run: ```
xtightvncviewer -bgr233 -compresslevel 9 -quality 0 example.server.com::5901
```Note: those two colons are not a typo! WIth TightVNC one colon indicates display number, two indicate port number.
[B]
For TIghtVNC 1.39[/B]
Download and install the deb I've attached to this post.
Run: ```
vncviewer -bgr233 -compresslevel 9 -quality 0 example.server.com::5901
```If you run into problems feel free to PM me.

---

### Post by SadaraX on 2008-03-27
I found a solution to this problem for myself a few months ago. I guess I forgot to reply here (I have seen this problem in several threads, so I can't get them all).

I run the tightvncserver for my VNC server. This works well. I limit the colors to 16 bit.

In the past years, I have used xtightvncviewer (and vncviewer). It worked good few a years.

But about a year ago, xtightvncviewer became slow, slow, slow, SSSSLLLLOOOOOOOWWW......

Well, I decided to try using KDE's vnc viewer called 'krfc'. I installed it, and configured the VNC settings to be as low as possible.

When I connected to my VNC, it suddenly was just as speedy as before. I can only assume the error is some bug in xtightvncviewer.

---

### Post by cyboc on 2008-06-11
> **process91 said:**
> Run: ```
xtightvncviewer -bgr233 -compresslevel 9 -quality 0 example.server.com::5901
```

For me, the magic incantation for xtightvncviewer was the combination of -bgr233 *and* -encodings "tight". For example:
```
xtightvncviewer -bgr233 -encodings "tight" -compresslevel 9 -quality 0 example.server.com::5901
```

If either option was missing, the performance was slow. With both options applied, it was at least as fast as the Windows tightvncviewer (I ran both clients side-by-side simultaneously).

Hope that helps.

---

