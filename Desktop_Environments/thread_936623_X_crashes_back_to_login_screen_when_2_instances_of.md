---
title: "X crashes back to login screen when 2 instances of glx apps (glxgears,..) are running"
date: 2008-10-03
forum: Desktop Environments
---

### Post by rbpember on 2008-10-03
Not sure if it's kosher to repost on another forum. I posted this last night under general help and got no replies. This forum looks more appropriate. My apologies if I've broken protocol. I've reattached 
all the relevant files here.
------------------------------------------------
This is a specific case of [http://ubuntuforums.org/showthread.php?t=935721](http://ubuntuforums.org/showthread.php?t=935721).
(running two instances of an x-app using glx and having X crash on me)

With glxgears, I just fire up 2 of them and X crashes, without fail.

The error is independent of gnome. I can fire up xinit (after ctrl-alt-f1),
enter

glxgears&;glxgears

at the shell prompt in the xterm and **BAM**, X crashes me back to the command prompt **EACH AND EVERY TIME** ] (*,)

I've attached the output from the X session.

At the risk of repeating:

Some details or my setup: I'm running Gutsy Gibbon (this is my work machine and I haven't had time to safely upgrade yet.) I have a Dell Precision M6300 laptop with an NVIDIA QUADRO FX1600M. Although the laptop has 64 bit processors, I had trouble getting the 64 bit OS to work, so I'm running the 32 bit OS. Also, I had trouble getting the full Nvidia drivers to run, so I'm not using any proprietary drivers.

My xorg.conf is attached to the other post.

See [http://ubuntuforums.org/showthread.php?t=935721](http://ubuntuforums.org/showthread.php?t=935721) for other detail.

I've seen some related posts about disabling glx. That's unfortunately not an option for me. I need it for some of my applications.

My workaround for now is obvious -- run only one of the guilty X apps at a time -- but it can be cumbersome and every once in a while I slip and
**bam** I back at the login window.

---

### Post by rbpember on 2008-12-09
I finally had some time to resolve this. The key issue was that I was running the Mesa drivers instead of Nvidia drivers. I tried running the unrestricted Nvidia drivers, but received  messages along the lines of my display not being a glx display when attempting to run a glx app. So, I took the path of least resistance, and am now running the restricted Nvidia drivers. (Not the Ubuntu way, I know, :icon_frown: )BTW, there's an excellent discussion on how to use TwinView (which is also Nvidia proprietary) at [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html#comment-157713](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html#comment-157713)

---

