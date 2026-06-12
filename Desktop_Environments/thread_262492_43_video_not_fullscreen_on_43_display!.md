---
title: "4:3 video not fullscreen on 4:3 display?!"
date: 2006-09-21
forum: Desktop Environments
---

### Post by Zunino on 2006-09-21
Hello.

First, some info about my setup: running Dapper; Totem 1.4.3 (using GStreamer 0.10.6) installed; video hardware is an nVidia 6600GT card with binary drivers installed (as per instructions on the Wiki site) and a regular 4:3 CRT monitor.

The problem: TV-aspect videos do not cover the screen area when in fullscreen mode. As an example, I have a 640x480 movie. When I go into fullscreen mode ('f' key in Totem), the video does occupy the whole of the vertical area of the screen, but there are quite noticeable black bars on the sides.

I have a reasonable understanding of why black bars are used when one plays, say, a 16:9 video on a 4:3 display. But what I have here is a 4:3 video playing on a 4:3 display, so I expected it to cover the whole screen area. Just FWIW, I noticed the video controls that show up when you move the mouse in fullscreen *do* take up the whole horizontal area. It's just the video that gets cut on the sides.

Is this a player problem? A driver one?

I would appreciate any input with regards to this matter.

Thank you very much,

-- 
Ney André de Mello Zunino

---

### Post by Kabatwa on 2006-09-23
Hi Zunino,

I think your problem may be to do with the aspect ratio that you're playing in totem. Tv's and other devices output to pixels that aren't square, they are in fact a rectangular shape so when you view images captured on a tv or other such device they can appear skewed due to your monitors pixels being square. Try in totem, going to View> Aspect Ratio and change it from Auto to either Square or 4:3 (TV).

Hope this helps!
Tim

---

### Post by Zunino on 2006-09-23
> **Kabatwa said:**
> Hi Zunino,

I think your problem may be to do with the aspect ratio that you're playing in totem. Tv's and other devices output to pixels that aren't square, they are in fact a rectangular shape so when you view images captured on a tv or other such device they can appear skewed due to your monitors pixels being square. Try in totem, going to View> Aspect Ratio and change it from Auto to either Square or 4:3 (TV).
Thank you very much for your suggestion, Kabatwa. However, the video image would not change; I tried all of TV, square and auto. When I tried 16:9, the image did fill the horizontal space, but it looked squished (obviously).

I think what I should do is try out some other video player and see if the issue is somehow related to Totem itself.

Thank you,

-- 
Ney André de Mello Zunino

---

### Post by Zunino on 2006-09-23
> **Zunino said:**
> I think what I should do is try out some other video player and see if the issue is somehow related to Totem itself.
I have installed the VLC media player and have been able to play the same 4:3 videos in actual fullscreen. This simple test might not be enough to conclude that Totem is at fault, but it gives indication in that direction.

-- 
Ney André de Mello Zunino

---

### Post by Kabatwa on 2006-09-24
I'm glad you've had some positive steps forward.
Do you need to use Totem or could you use VLC? Totem is my player of choice but when that fails I go to VLC as it seems quite capable indeed! Let me know of any progress you make if you don't mind. Seems like and interesting problem and I'd be happy to find out what it was.

Tim

PS. Have you tried editing the video quickly in Kino or Avidemux to see if you can change any details?

---

