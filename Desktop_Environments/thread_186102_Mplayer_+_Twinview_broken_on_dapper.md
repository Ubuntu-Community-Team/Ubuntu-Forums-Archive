---
title: "Mplayer + Twinview broken on dapper?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Termina on 2006-06-01
Just dist-upgraded from 5.10 to Dapper, and everything is working fine so far expect mplayer.

I'm using the same xorg.conf file as before, and I installed the nvidia-glx package (and compiled the nvidia-kernel package that was placed in /usr/src)

However, when I fullscreen mplayer on the TV screen, it now only shows a small portion of the video. (so only 1/4 of the video is shown, or something similar).

Does anyone know how to fix this?

---

### Post by mcpish on 2006-06-01
It seems like you use mplayer in almost exactly the same way I do.  
I also have an Nvidia card (GeForce 6200) with twinview TV out that I use mplayer for to play video files full-screen on the TV.

I have no problems playing them.  I know what problem you are referring to though, I've seen it before.  You are missing a video output module in mplayer so you need to change the video output driver to something else you have installed like xv or gl. 

Do the following:
1. Type "sudo gedit ~/.mplayer/config" and enter your password when prompted
2. Add either one of the following lines to the end of the file without the quotes, "vo=gl" or "vo=xv"
3. save the file
4. now play your file and see if it fixes it

---

