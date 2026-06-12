---
title: "Recommended Video Capture Program?"
date: 2012-01-23
forum: Gaming &amp; Leisure
---

### Post by TurtleKing on 2012-01-23
I'm looking into doing free promotions for Linux games such as FlightGear and 0 A.D. However, I'm not sure what is a good screen capture program for Ubuntu Games. In Windows I would just fire up fraps, and start recording. So is there a good screen capture that is close if not equal to Fraps for Windows? Also, it would be awesome if it was available for free (free games that are playable in Linux is the theme).

I tried GLC, but the installation always gives me an error related to the developer.

---

### Post by Arthur_D on 2012-01-23
GLC or good ol' ffmpeg is what I've used so far with best results. Both aren't particularly user-friendly, so in that regard: no, there is no Fraps alternative (never used it, but allegedly it has a graphical user-interface AND produces good quality videos, whereas the Linux programs I've tried has either a GUI or produces acceptable quality videos).

---

### Post by ubudog on 2012-01-23
+1 for GLC.  

See this post for info on how to use it.  :)

[http://ubuntuforums.org/showpost.php?p=11037745&postcount=8](http://ubuntuforums.org/showpost.php?p=11037745&postcount=8)

---

### Post by FakeOutdoorsman on 2012-01-23
If you want to try FFmpeg see [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

---

### Post by TurtleKing on 2012-01-24
> **ubudog said:**
> +1 for GLC.  

See this post for info on how to use it.  :)

[http://ubuntuforums.org/showpost.php?p=11037745&postcount=8](http://ubuntuforums.org/showpost.php?p=11037745&postcount=8)

Can you do a quick recap on what is needed to install? The instructions are bit confusing on github.

Operating System: Ubuntu 11.10 64bit

---

### Post by TurtleKing on 2012-01-26
> **ubudog said:**
> +1 for GLC.  

See this post for info on how to use it.  :)

[http://ubuntuforums.org/showpost.php?p=11037745&postcount=8](http://ubuntuforums.org/showpost.php?p=11037745&postcount=8)

Still not working.

username@computer:~$ glc-capture --resize=0.5 -s -o video /usr/games/fgfs 
glc-capture: command not found
username@computer:~$

---

### Post by TurtleKing on 2012-01-26
> **FakeOutdoorsman said:**
> If you want to try FFmpeg see [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

Awesome program and It works! :D

Here have some virtual cookies:
[IMG]http://artfullydangerous.com/wp-content/uploads/2011/06/cookies.jpg[/IMG]

---

