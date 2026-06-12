---
title: "[SOLVED] Terminal Server Client full screen mode in one workspace"
date: 2008-01-21
forum: Desktop Environments
---

### Post by MountainX on 2008-01-21
Terminal Server Client full screen mode in its own workspace:

I'd like to have 1 of my 2 workspaces dedicated to a connection to my Windows XP box using the Terminal Server Client program running in full screen mode. Of course, when in full screen mode you have no window decorations that you can use to iconify the Terminal Server Client program when you are ready to come back to "linux land". You generally have to hit Ctrl-Alt-Enter to force the window manger to slap a box around the full screen window so that you can iconify it or move to another workspace. However, you can hit Ctrl-Alt-<arrow key> to move to another workspace if in the Terminal Server Client settings you put a check mark in the "Enable window manager's key bindings" box of the "Performance tab. However, the problem here is that when you do the Ctrl-Alt-<arrow key> to move from the full screen "Windows workspace" to a "Linux workspace" you'll find that while you are indeed changing workspaces the full screen Terminal Services Client screen is following you. So when you relent and hit Ctrl-Alt-Enter you are now in some other workspace but the Terminal Services Client is running there now. What I'd like is for it to stay in the workspace that I put it in and when I hit Ctrl-Alt-<arrow key> I'm in some other workspace with my linux desktop ready to go. Anyone know how to make this happen? Thanks y'all!

(This whole question comes from the following link. It states my case exactly, so I reused the question.
[http://forums.fedoraforum.org/showthread.php?t=42186](http://forums.fedoraforum.org/showthread.php?t=42186))

The proposed solution here doesn't work for me because it isn't really using full screen mode:
[http://ubuntuforums.org/showthread.php?t=658355](http://ubuntuforums.org/showthread.php?t=658355)

---

### Post by jeffus_il on 2008-01-21
How about running two X-Servers, so you would have one on <Ctl-Alt-F7> and the second on <Ctrl-Alt-F8>, there are threads on the forum explaining how to do it, If not I can post.

---

### Post by MountainX on 2008-01-21
> **jeffus_il said:**
> How about running two X-Servers, so you would have one on <Ctl-Alt-F7> and the second on <Ctrl-Alt-F8>, there are threads on the forum explaining how to do it, If not I can post.

I am new to Linux, so I haven't heard of this. However, it sounds like a good idea. My desktop setup uses dual monitors with an nVidia card & twinview enabled. Can I have two X-Servers, each set up this way?

Also, since the MS Windows Server machine in the full screen remote desktop session captures <Ctrl-Alt-Arrow> keys, will it not also capture <Ctrl-Alt-F8>?

---

### Post by jeffus_il on 2008-01-22
I think you can, the ATI config utility once did it on ATI, I haven't done it, I'm sure it's possible, I will check it out, and get back to you if someone else doesn't beat me to it, hopefully they will.
You can open another X Server with something like ```
Xorg -d :1.0 &
``` and then ```
myprog -d :1.0 &
```That's the idea, untested.

---

### Post by MountainX on 2008-01-22
Thank you. I'll be awaiting more info.

---

### Post by jeffus_il on 2008-01-23
Do this manually first, it can be automated later.

To run an XServer on <Ctrl-Alt-F8>
Open a console using <Ctrl-Alt-F1>
Login with Username and Password
Type the command ```
sudo Xorg :1.0 &
```Move to the new X Session using <Ctrl-Alt-F8>
Can you see the XSession?
Now you have to run a program on the new server.
Again, Open a console using <Ctrl-Alt-F1>
And run the program of your choice, for example I will run the gnome-terminal.
```
 gnome-terminal --display :1.0 &
```Again <Ctrl-Alt-F8>
You don't have a window manager, so run this in the new Gnome terminal.
```
metacity &
```Now we can think about automating this in a script.

---

### Post by MountainX on 2008-02-03
I have a working solution that was very easy:

From a full screen RDP session:
Ctrl-Alt-Enter exit full screen mode. 
Ctrl-Alt-<arrow key> to switch desktops
... then later
Ctrl-Alt-<arrow key> to return to original desktop
Ctrl-Alt-Enter return to full screen mode

That's it. Works pretty well.

---

### Post by sshetty on 2008-03-04
Another easy way is to minimize the Terminal Server Client to the Panel; then right click on it and change its property from 'Always on Visible Workspace' to 'Only on This Workspace'.

---

