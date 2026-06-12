---
title: "Is VNC connection supposed to look like this?  No full GUI?"
date: 2006-07-31
forum: Desktop Environments
---

### Post by KillrBuckeye on 2006-07-31
I just started messing around with VNC using tightvnc, and I was disappointed to see that the remote connection window looks like the attached image.  (I am using the TightVNC Windows client to connect to my Ubuntu machine running the TightVNC server.)  Compared to Windows Remote Desktop, this is disappointing.  Where are my menu bars, icons, etc.?  Is this not supported over VNC, do I need a different server/client, or what?

[IMG]http://i7.photobucket.com/albums/y299/KillrBuckeye/tightvnc.jpg[/IMG]

---

### Post by rich.bradshaw on 2006-07-31
It shouldn't look like that - I have only ever used KDE, but the k remote desktop via VNC works as if you wre in front of the pc.

---

### Post by KillrBuckeye on 2006-07-31
Thanks.  Can anyone tell me why this might be happening?  If I start up an application from the command line, such as Firefox, it looks fine.  So where is my regular desktop?

rich: Do you recall what VNC program you were using?

---

### Post by Lord Illidan on 2006-07-31
From Windows i rememeber using Tight VNC, try that instead. I could get a full Ubuntu desktop...

---

### Post by KillrBuckeye on 2006-07-31
I am using TightVNC Windows client.

---

### Post by Lord Illidan on 2006-07-31
Oops, sry about that.

Can you show us a screenshot of your connection options under Windows, and under Ubuntu?

---

### Post by KillrBuckeye on 2006-07-31
NP.  I'm at work right now so I won't be able to check anything.  I can tell you that in Ubuntu I simply started up the TightVNC server via:

% sudo apt-get install tightvncserver
% tightvncserver

In Windows, I tried connecting using the TightVNC client with both bandwidth options.

---

### Post by KillrBuckeye on 2006-08-01
Well, I gave up on using TightVNC and instead used the following guide to set up vnc4server.  It seems to be working great.  Thanks for your help.

[http://www.ubuntuforums.org/showthread.php?t=191564&highlight=ssh+tunnel+vnc]("http://www.ubuntuforums.org/showthread.php?t=191564&highlight=ssh+tunnel+vnc")

---

