---
title: "Dgen locking up"
date: 2008-05-29
forum: Gaming &amp; Leisure
---

### Post by denham2010 on 2008-05-29
Hi,

I'm having a problem with Dgen. It was working perfectly with Gutsy, but since my upgrade to Hardy, trying to run a game just ends up with a black window and Dgen being locked up.

Running from the command line gives no errors, but because it locks up, I'm thinking any output is not getting through to stdout. I can't even CTRL+C in the terminal to terminate the application. I either have to close the terminal window, or kill the application through my System Monitor.

Thinking it may be an issue with compositing and compiz (as was the case with Feisty), I disabled all the bling and reverted to my default window manager (XFWM4 - running Xubuntu here). Same issue.

I have also tried downloading Gens, but that is doing exactly the same thing. Upon running, I just get a black window (no sounds or anything) and it all just locks up. No errors from running in the terminal,and can only be killed with System Monitor or closing the terminal (even opening another tab in the terminal and trying killall [processname] doesn't kill it!)

Now, just to be clear (or unclear as the case may be) I am uncertain if this began after the upgrade to Hardy, or the upgrade to PulseAudio (pulse did not install by default in my upgrade, but it certainly fixed a lot of sound issues I was having after the upgrade).

Has anyone else experienced this problem, and/or does anyone know of a fix or at least the cause? I just wish I could get some sort of output from running in the terminal to have some idea of what is going wrong!

Thanks.

---

### Post by acoustibop on 2008-05-29
As far as GENS is concerned, denham2010, try [this .deb]("http://ubuntuforums.org/showpost.php?p=4997623&postcount=329") recently posted by megamaced.  He's included a patch written by MonkeeSage in it which fixes the segmentation fault that many people, myself included, were getting.

---

### Post by denham2010 on 2008-05-30
Thanks for that. I have tried the updated Gens, but still no go unfortunately.

It's really frustrating that I'm not getting any output whatsoever to indicate what the problem may be.

---

### Post by denham2010 on 2008-06-08
Well it appears it was something in the kernel causing the problem.

After the latest kernel upgrades, dgen is now working again.

---

