---
title: "Xubuntu video very choppy - Older system - Need expert opinion"
date: 2008-04-01
forum: Desktop Environments
---

### Post by rashead on 2008-04-01
I installed Xubuntu on my older PC and the install worked fine, and the applications start relatively quickly (for an older PC)

The problem I have is that streaming video (all video really) is very choppy - Close to 1 or 2 frames per second.  The sound is OK

I'm thinking that Xubuntu should work for older systems, but maybe my video card can't handle the video???  I was thinking about switching to something like Puppy Linux or Fluxbuntu in hopes that it would be better.

Let me know what you think, am I missing some configuation somewhere?  This is what I know:
500Mhz Celeron Processor
256MB RAM (max for the system)
20GB Hard Drive
Video: Intel 82810-DC100 Graphics Controller 

The correct driver is showing in the xorg.conf file for the video, and there is nothing showing in restricted drivers.

I appreciate your help/opinions - Thanks in advance.

---

### Post by rashead on 2008-04-02
Well, Fluxbuntu does the same thing with the video.  I did forget to mention that another problem with the Xubuntu is that when going into Terminal, the X Server restarts??

The problem with X doesn't seem to be happening with the Fluxbuntu system, but I still have the video problem.  I guess if I don't get any responses, I'm going to try Puppy or maybe PCFluxBoxOS

Thanks

---

### Post by stefangr1 on 2008-04-02
What kind of video are you trying to play?

Can you post your cpu usage (for example by running top) when your player is at work?

---

### Post by mali2297 on 2008-04-02
> **rashead said:**
> Well, Fluxbuntu does the same thing with the video.  [color="blue"]I did forget to mention that another problem with the Xubuntu is that when going into Terminal, the X Server restarts??[/color]

The problem with X doesn't seem to be happening with the Fluxbuntu system, but I still have the video problem.  I guess if I don't get any responses, I'm going to try Puppy or maybe PCFluxBoxOS

Thanks

This is known bug in xfce4-terminal, see
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849)

There are some workarounds posted below the bug report. An alternative is to change preferred terminal emulator to xterm (installed by default) or whatever terminal you like.

---

### Post by rashead on 2008-04-02
Thanks for the info on the terminal bug.  I'm glad that seems like a fairly easy workaround.

As for what video it is happening with, it's all video.  After doing some more poking around the internet, I believe it's just a video card problem with Linux as several people have had problems with this video card on several different distros.  I'm going to try to add a VideoRam value into my xorg.conf file when I get home tonight.  We'll see, I'd like to stay away from Windows, but I may just end up installing Win2000 on it if that doesn't work.

Thanks for your help

---

