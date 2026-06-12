---
title: "Planeshift fatal error (opengl related)"
date: 2007-05-28
forum: Gaming &amp; Leisure
---

### Post by topsites on 2007-05-28
Ubuntu Feisty Fawn 7.04

Ok, I downloaded and installed planeshift, all went well, desktop icons and all.

But if I click on either the Setup or the Client icon, I get a small rectangle box with the heading Fatal Error.
Inside the box it says:
crystalspace.graphics3d.opengl:  Error opening Graphics2D context.

And an Ok button...

Any ideas?

---

### Post by merlyn on 2007-05-28
Out of curiosity, which release of Ubuntu, kernel version, and video drivers are you running?

The reason that I ask is that until yesterday, Planeshift was running fine for me.

However since a recent upgrade I have experienced some problems, which initially began with the following error message after a reboot.

```
/bin/sh: can't access tty; job control turned off
```Followed by an "(initramfs)" prompt.

A search for this problem has revealed a range of different 'fixes', none of which have worked for me, other than installing the 386 kernel.

So far I have been unable to pinpoint the exact problem. 

However since then I have been unable to get the nividia drivers working, a number of applications are misbehaving, including the same problem with Planeshift that you mention.

I'm running Feisty by the way.

Cheers.

_**Edit:**_ For what it's worth, I have found a resolution to this problem for my install. I have been able to boot successfully into a later kernel version, and install the nvidia-glx drivers. Planeshift and other games that I was experiencing problems with are now working.

Cheers.

---

