---
title: "Create launcher"
date: 2012-06-24
forum: Desktop Environments
---

### Post by UnkleRay on 2012-06-24
Hi all,
My first post. Using Ubuntu 12.04 64 bit. I've found popping this into terminal 

ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 30 -qscale 1 -i :0.0 ./Desktop/mydesktop.mkv

an excellent way to record my desktop. I was just wondering if there was a way to create a launcher that will open terminal and pop this text into it to start the recording?

---

### Post by MG&amp;TL on 2012-06-24
Woo, first post, welcome!

Okay, install the *main menu* app from the software centre. Then open it, and make a new launcher, putting this command as the command field:

```
x-terminal-emulator -e "ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 30 -qscale 1 -i :0.0 ./Desktop/mydesktop.mkv"

```

---

### Post by black veils on 2012-06-24
use this method, for your purpose, it should work the same way. the point is you are not just able to make a launcher for this function, you are needing to run a command, which requires a script in the process too. its easy enough really:

[http://ubuntuforums.org/showthread.php?t=2007247](http://ubuntuforums.org/showthread.php?t=2007247)

change the relevant command etc for your task!

---

