---
title: "Correct kernel and unrelated VLC issues"
date: 2005-09-26
forum: Desktop Environments
---

### Post by Skye on 2005-09-26
Hello all- two questions for you.

First, I have a AMD 64 processor, but i'm currently running a 32 bit Ubuntu kernel.  Which of the availible kernels would provide the best performance?  The specific k8 kernels seem to be availible only for 64 bit linux, and I'm not sure whether to run the 686, 386 or k7 variations of 2.6.10-5.  Does it matter?

Secondly, I run a dual-monitor setup.  It works perfectly well, except that I cannot get VLC to play fullscreen DVD movies in my right-hand monitor, no matter what I do.  If anyone could offer a way around this, I'd be very grateful- is there a way to do it in VLC, or is there a different program that would do it better?

Thanks!

---

### Post by mlomker on 2005-09-26
> k7 variations of 2.6.10-5.  Does it matter?

The specific kernels just use a little less memory.  You'd want to use k7, which I believe is optimized for Athlon XP.

> 
Secondly, I run a dual-monitor setup.  

I did some searches on Google but didn't come up with a lot.  To clarify, you have two monitors with separate desktops on them (not cloned).  You open a command prompt on the second one, launch VLC, but the video is played on the first monitor?

I need to set up a dual-monitor desktop one of these days so that I can see how these things work.

---

### Post by Skye on 2005-09-26
Thanks for the help!

You're correct as to my setup- to be more specific, VLC plays on both sides when not in fullscreen mode, but when fullscreen is enabled, it automatically plays the fullscreen on the left screen, no matter the placement of the vlc window itself.  I'm asking this question in the forums because I couldn't find any relevant data via google, archived forum posts, the wiki, or the VLC site.

---

### Post by mlomker on 2005-09-26
What are your video card(s)?  This could be a driver-specific thing.

---

### Post by Skye on 2005-09-26
I'm running a nvidia 6800GT with dual heads.  The driver is the latest nvidia driver availible from the nvidia website.

---

