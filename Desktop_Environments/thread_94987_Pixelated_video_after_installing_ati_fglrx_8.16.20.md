---
title: "Pixelated video after installing ati fglrx 8.16.20 (Pls take a look)"
date: 2005-11-25
forum: Desktop Environments
---

### Post by PrimoTurbo on 2005-11-25
[Here]("http://img497.imageshack.us/img497/2987/screenshot13ce.jpg") is a screenshot of what I mean. I know the video is bad quality but it's very obvious that it's very pixelated. Before I installed fglrx I was using the ati driver which has no 3d support. I was able to play the same video with no pixelation. I have tried totem, mplay and vlc and they all have the same problem.

I know the driver works I'm getting over 4k with glxgears -iacknowledgethatthistoolisnotabenchmark

I followed this guide to install the driver - [http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378)

What's the problem here? I had a similar problem when I installed ubuntu a several months back, I was using an older version of fglrx but the exact same problem.

I'm on a 9700 Pro btw.

I really need 3d support but I also want to watch clear videos, any ideas or suggestions? Thank you.

---

### Post by SergioG on 2005-11-26
I have the same problem with my Asus AX800PRO. Can someone help us?

Bye

---

### Post by mlomker on 2005-11-26
You'll probably want to ask the question on the [ATI board ]("http://www.rage3d.com/board/forumdisplay.php?f=92")unless you're sure this is only a problem with Ubuntu (it works for you on another linux distribution with the same driver).  It is well known that the fglrx driver has worse 2D performance than the ATI driver.

---

### Post by PrimoTurbo on 2006-05-08
It's fixed on Dapper, but totem still has issues with flickering. So I use mplayer and select the opengl under video prefernces don't use x11 to render the video.

---

