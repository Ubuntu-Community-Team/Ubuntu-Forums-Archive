---
title: "XGL Taking lots of resources, running slowly"
date: 2007-03-08
forum: Desktop Environments
---

### Post by Angafirith on 2007-03-08
I have been running XGL under Edgy Eft for quite some time now, but I only recently started having serious issues with it. After a while in an XGL session, my desktop environment slows down to the point that it becomes unusable. I experience slow scrolling in firefox and slowness when I try to alt-tab, among other things.

Thinking that the problem might be with Beryl, I tried using metacity with XGL for a while. I had the same issues. I tried running a normal X session without XGL, and it worked perfectly fine for me. I tried updating my FGRLX driver to the latest version, to no avail.

I never really paid attention to the CPU utilization of XGL before, but recently it's been in the 50-75% range most of the time.

Unfortunately, I am one of those poor Radeon Xpress 200M IGP owners that can't use the open source drivers. As a result, I can't use AIGLX to get composited effects. I keep reading topics about my hardware being broken under feisty (also an unfortunate bcm4318 owner), so I don't want to risk upgrading.

As for technical information:

I use the following script to start XGL: 
```
#!/bin/bash
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:fbo & sleep 2
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
export DISPLAY=:1
DISPLAY=:1 gnome-session

```
I have GDM setup to run this script as a session, so that I can choose to use plain old X when I experience these difficulties. I had just been contemplating changing to the other method when all of this happened.

I'm using XGL version 7.0.0.git.20060725-0ubuntu2.1 from beryl's repositories. I have no idea whether this is different from the version in edgy universe or not.

I can't think of any changes I made to my system recently. I did try backporting some mesa packages from feisty, but never installed them.

EDIT: It just occured to me that my gnome-panels have also been crashing a lot recently under Xgl, but I don't think they were under normal X.

---

