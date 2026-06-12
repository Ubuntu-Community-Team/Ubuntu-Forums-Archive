---
title: "gnome-panel problems after maximized window"
date: 2010-11-02
forum: Desktop Environments
---

### Post by BCingyou on 2010-11-02
Although I've seen a number of threads about basic problems with the gnome-panel, I haven't found quite this problem.  This is NOT just a thread about accidentally deleting a panel and restoring it, I have looked through tons of those and none have addressed my problem.  

It all started innocently enough... I opened Xmind (a brainstorming/mindmap application) and the window automatically went to fullscreen.  When I resized it, not only were the gnome panels gone, but I was completely unable to restore them.  And the panels continue to attempt to launch again and again but fail.  

This happens about 50 times a minute, meaning everything on the desktop jumps up and down constantly as it gets realigned. 

I have tried this fix, a shell script someone wrote to restore the default panels:

[http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

It doesn't do anything for me.  

I also tried these terminal commands:

```

gconftool-2 –-shutdown
gconftool –-recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

Everyone says these work like a charm for most gnome-panel issues but they do nothing for me. :confused:

I'm obviously no power user but I've been using ubuntu for almost 2 years and have never run across a problem like this.  I simply cannot get the panels to return to normal form and it's messing up every other part of the GUI.  The constant attempt to launch the panels steals focus from the other windows, meaning even using the browser doesn't work too well (I'm writing this from a different computer).

Help me O Great Gurus of Linux Computing! :frown:](*,)

(Oh re: hardware/software I am using 10.10 and it's on a custom-built PC with ATI graphics card if any of that matters).

Thanks in advance.

---

### Post by BCingyou on 2010-11-02
bump please help, this may not sound like much of a problem but it's messing up my entire desktop and all of the obvious fixes that work for everyone else are failing.

---

