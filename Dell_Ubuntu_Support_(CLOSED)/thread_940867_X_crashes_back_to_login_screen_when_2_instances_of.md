---
title: "X crashes back to login screen when 2 instances of glx apps (glxgears,..) are running"
date: 2008-10-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rbpember on 2008-10-07
Not sure if it's kosher to repost on another forum. I posted this on two other forums (General and Desktop Environments) and haven't received any replies. My apologies if I've broken protocol. I've reattached
all the relevant files here.
------------------------------------------------

If I run two instances of an X applications using glx, X crashes on me.

A specific case: with glxgears, I just fire up 2 of them and X crashes immediately without fail. With other applications that use glx, the crash
is inevitable but not always immediate.

The error is independent of gnome. I can fire up xinit (after ctrl-alt-f1),
enter

glxgears&;glxgears

at the shell prompt in the xterm and ****X crashes me back to the command prompt each and every time.

I've attached the output from the X session.

Some details or my setup: I'm running Gutsy Gibbon (this is my work machine and I haven't had time to safely upgrade yet.) I have a Dell Precision M6300 laptop with an NVIDIA QUADRO FX1600M. Although the laptop has 64 bit processors, I had trouble getting the 64 bit OS to work, so I'm running the 32 bit OS. Also, I had trouble getting the full Nvidia drivers to run, so I'm not using any proprietary drivers.

My xorg.conf is in rbpember_100108.tar.gz

I've seen some related posts about disabling glx. That's unfortunately not an option for me. I need it for some of my applications.

My workaround for now is obvious -- run only one of the guilty X apps at a time -- but it can be cumbersome and every once in a while I slip and
**bam** I back at the login window.

---

### Post by rbpember on 2008-12-09
I finally had some time to resolve this. The key was that I was running the Mesa drivers instead of Nvidia drivers. I tried running the unrestricted Nvidia drivers, but received  messages along the lines of my display not being a glx display when attempting to run a glx app. So, I took the path of least resistance, and am now running the restricted Nvidia drivers. (Not the Ubuntu way, I know, :icon_frown: )BTW, there's an excellent discussion on how to use TwinView (which is also Nvidia proprietary) at [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html#comment-157713](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html#comment-157713)

---

