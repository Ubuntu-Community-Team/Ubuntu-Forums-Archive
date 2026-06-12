---
title: "Video Playback Problem"
date: 2006-09-13
forum: Desktop Environments
---

### Post by zentagonist on 2006-09-13
I have a slightly older laptop (Dell Inspiron 6000), on which I installed Ubuntu (6.06.1).  I got all the hardware working great, and only have one issue at this point.  Video playback will only work properly right after a fresh boot.  
     Here's the issue: everything will play fine, even right through a playlist. But as soon as I exit the player, the NEXT time I play a video, it looks as if it is playing back in 8-bit color mode.  
     The player does not matter (I've tried VLC, Totem, Xine, and Mplayer), neither does the video file type (with the w32codecs it happens with wmv's, mpg's, avi's ... and it also happens with the example .ogg video that is avaliable on a fresh install).    
     I can "fix" the issue temporarily by logging out, then back in. Which is a pain.  I have no other video/resolution/monitor issues, and GL applications also have no trouble. 
Here are some example "screenshots" of the issue. This first one is right after a fresh login: 

[IMG]http://static.flickr.com/83/242267666_d6dbc44376.jpg[/IMG]

And this one is after I exit Totem, then open the same exact video file:
[IMG]http://static.flickr.com/85/242267667_181f3a750a.jpg[/IMG]

(I put "screenshots" in quotes because I couldn't get a proper screenshot using any of the "traditional" means, and only have my cameraphone with me at the time of this post)

Any help would be greatly appreciated.

---

### Post by zentagonist on 2006-09-13
seriously ... any ideas?

---

### Post by jcrnan on 2006-09-13
I dont have a clue what could be wrong but try opening it both times via the terminal and then closing it again and post any error logs you get here.

---

### Post by g4c9z on 2006-09-13
I'm likewise clueless, but maybe your kernel logs would tell you something.  I think it's /var/log/messages that often gives you error messages that you don't otherwise find out about.  Look at the end of it just after trying to watch a video each time.

---

### Post by zentagonist on 2006-09-14
Looking at the logs, and opening via the terminal didn't really give me any clue.  But I DID get the problem fixed.
     I opened Xine, and noticed that the problem would go away if I changed the video driver setting to something like OpenGL (instead of xv, or xvmc).  However, while Totem-xine is installed, changing that setting made no difference in VLC, Totem, or mplayer.  But it did give me an idea.  A quick read-through of the mplayer man pages gave me a solution.  
     I edited the driver line in /etc/mplayer/mplayer.conf from "vo=xv,sdl,X11" to "vo=X11,gl2" ... problem fixed.  Apparently, xv wasn't a fan of this laptop.

---

