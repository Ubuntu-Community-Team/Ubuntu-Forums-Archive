---
title: "Ssh vnc?"
date: 2011-05-26
forum: Desktop Environments
---

### Post by Duvrazh on 2011-05-26
All,

Installed Ubuntu Server on a headless machine. I'm not saavy enough to configure all the different things I need from it with just the command line and need to use the desktop. I ran the following ```
sudo apt-get install gnome
``` and it installed the basic gnome desktop.

I'm having trouble viewing this desktop. I've tried running ```
sudo x11vnc -create -safer -localhost -nopw -once -display :0 -auth guess
``` to create the desktop and in a separate Putty ```
ssh -X -C *user*@*machine*
``` followed by ```
vncviewer localhost:0
```. Resulting error is Error: Can't open display: localhost:12.0.

Worked three times out of countless times. What am I doing wrong? Additional info: Putty from Windows 7 into server.

---

### Post by krunge on 2011-05-26
I don't think you want to run the vncviewer on the REMOTE machine, you want to run it on the computer you are sitting at. This will give the best performance, especially going over a non-LAN network link.

Let 'sittinghere' be the name of the unix computer you are sitting at. and let 'user' be your username on the remote machine named 'machine' in your example.  "sittinghere>" and "machine>" indicate shell prompts on the respective computers.

Here is one way to do it:
```

Terminal #1

sittinghere> ssh -L 5900:localhost:5900 -C user@machine
machine> sudo x11vnc -safer -localhost -nopw -once -display :0 -auth guess

Then in Terminal #2 (a 2nd window)

sittinghere> vncviewer :0

```

That should work.  It is easy to automate this in a shell script see:
[INDENT][http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)[/INDENT]
for that and other ideas.  Also the x11vnc companion viewer hack named SSVNC will do this for you automatically on all platforms.

PS: I don't know exactly why your "vncviewer localhost:0" (run on remote machine!!) got the error "Error: Can't open display: localhost:12.0" but I can help you if that is what you really want to do...

---

