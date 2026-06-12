---
title: "Remote Control of Desktop"
date: 2013-12-05
forum: Desktop Environments
---

### Post by Andrew_Perry on 2013-12-05
I'm trying very hard to remotely control my Ubuntu 12.04 Desktop from a Windows 7 Desktop. I've tried a number of solutions and they all seem to be beset with problems.[IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG] I've tried looking online for solutions but so far to no avail. Here is a summary of what I have tried:-

1. vino - get a black screen.
2. x11vnc - displays the desktop OK but will not respond to any keyboard or mouse actions.
3. tightvnc - desktop shows icons but no launcher bar.
4. xrdp - get a completely blank desktop with only the background image.

On Windows I was using RealVNC to try items 1-3 and Remote Desktop Control for item 4.

Before I try and progress any further and maybe waste time on unworkable solutions, can anyone please advise me as to what might be the easiest one to get working or even suggest a better solution.

Thanks,

Andrew.

---

### Post by The Spectre on 2013-12-05
I use TeamViewer and it has worked well for me...

[http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)


Here is a small Review of TeamViewer 9...

[http://www.webupd8.org/2013/12/remote-desktop-tool-teamviewer-9.html](http://www.webupd8.org/2013/12/remote-desktop-tool-teamviewer-9.html)

---

### Post by bashiergui on 2013-12-05
puTTY would let you control Ubuntu from windows assuming you have an ssh server running on Ubuntu. That will be entirely command line, though.

---

### Post by sammiev on 2013-12-06
Both work great but for easy of use I like TeamViewer.

---

### Post by QIII on 2013-12-06
If you want to go through the trouble of setting it up, feel like you can get a handle on SSH and use keys instead of passwords, NoMachine NX has a Windows client.  Set up your Ubuntu server (nx server, that is) and the graphical performance is very nearly native.

NX doesn't do all the bitmap repainting business VNC does.  It actually communicates X commands, so there is little network load or latency.

---

### Post by ian-weisser on 2013-12-06
> **Andrew_Perry said:**
> 
2. x11vnc - displays the desktop OK but will not respond to any keyboard or mouse actions.
3. tightvnc - desktop shows icons but no launcher bar.


I've had solid performance for years with both of those.

---

