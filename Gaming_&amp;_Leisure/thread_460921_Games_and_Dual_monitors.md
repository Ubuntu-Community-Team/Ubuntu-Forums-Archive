---
title: "Games and Dual monitors"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by Sunforge on 2007-06-01
I've been using Ubuntu for about two months now. I've got the desktop pretty much straightened out, with dual monitors 1600 x 1200, NVIDIA driver and I can get pure Linux games up and running. So far so good. I'm now trying to get a handle on the best option for quickly shutting down one monitor to play a game or to maintain both monitors as separate entities so that you can play a game in one window and keep an eye on the outside world in another.

I've read the thread on:

[http://ubuntuforums.org/showthread.php?t=441249&highlight=Games+Dual+monitors](http://ubuntuforums.org/showthread.php?t=441249&highlight=Games+Dual+monitors)
[http://ubuntuforums.org/showthread.php?t=437463&highlight=Games+Dual+monitors](http://ubuntuforums.org/showthread.php?t=437463&highlight=Games+Dual+monitors)

Both of these threads point to editing xorg.conf and putting in the following monitor resolution options (clearly I'm going to have to change to 1600 x 1200 to make it work for my setup):

Option "MetaModes" "1280x1024,1280x1024;1280x1024,1024x768;1280x1024,NULL;1152x864,NULL;1024x768,NULL;1280x1024;1280x1024+1200+0"

Now I get 1280x1204, 1280x1024 which sets both monitors to the same res
I can see 1280 x 1024, NULL - does this mean that the second monitor is now OFF?
I don't get what 1280x1024+1200+0 - what does this option do.

First off - what's the meaning and function of the NULL and + options?

If there a good explanation out there on the interweb that details the meaning and function of options for metamodes?

---

### Post by DJMatty on 2007-06-01
I seem to remember reading somewhere that the + specifies an offset, so you can make monitor 2 be on the left or right of monitor 1 by using offset values. 

DFP1: 1600x1200+0+0 DFP2: 1600x1200+1600+0 should put DFP2 to the right of DFP1

I'll try to dig out the post where I read it. I think it might be specific to the nvidia driver and part of twinview, and not a standard thing in xwindows (although I may be wrong on this :))

Matt

---

### Post by Sunforge on 2007-06-01
It would make sense to have an offset to specify which side the second monitor shows up, although I have to confess that I just switch the monitor cables around DOH! I got into the habit when using Windoze in earlier versions when anything could happen when you started mixing graphics cards.

Anyone have any ideas about the NULL - does this switch the second monitor off or does it leave it running but not display anothing on it?

---

### Post by DJMatty on 2007-06-01
Hi

I found this on the nvidia site that details what the values mean :)

[http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html](http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html)

HTH

Matt

---

### Post by DJMatty on 2007-06-01
Yeah it looks like the NULL will turn off the display for that metamode. Although it does say 'if you want the device to not be active' as to if that means turn off or just display nothing I don't know. I'd hope it means turn off :)

Matt

---

### Post by Sunforge on 2007-06-01
That's a pretty neat explanation posted on the NVIDIA web site thanks for finding it. I will have to digest this over the weekend.

I'm not terribly strong on unix but generally if you're routing something a null interface means it goes nowehere, so perhaps it redirects the second display to the bin, which is an interesting way of doing things.

If anyone out there knows what null means in the context of configuring twin view, it'd be interesting to find out if only to satisfy my sense of curiosity.

Thanks for all your help so far, I should be able to get a little further now.

---

### Post by Sunforge on 2007-06-02
Summary: the NULL statement works just fine. I can now switch one monitor off for gaming and have dual monitors for my normal stuff. Works like a charm. Way easier than windows. Nuff said.

---

### Post by lingenfr on 2007-06-02
> **DJMatty said:**
> Hi

I found this on the nvidia site that details what the values mean :)

[http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html](http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html)

HTH

Matt

Does anyone know if this information also applies with bigdesktop as well as twinview?

---

