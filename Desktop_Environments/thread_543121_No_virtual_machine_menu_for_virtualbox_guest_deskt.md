---
title: "No virtual machine menu for virtualbox guest desktop"
date: 2007-09-04
forum: Desktop Environments
---

### Post by ubukool on 2007-09-04
Hi everyone,

I'm running Feisty as host and Windows XP as the guest machine on virtualbox.  I was trying to figure out how to share between host and guest machines and read that I have to install the guest additions package, which you can do from the virtual machine menu....well, I looked at some screenshots but they look nothing like mine!  When I run XP it doesn't appear in a virtualbox window, it appears to be fullscreen and there's no virtual machine window with options like 'devices' etc, so I'm totally unable to install the guest additions.  Maybe I'm doing something stupidly wrong.  I've searched on Google for a similar problem but there are none.   Why does mine look different?

Does anyone have any advice?  Much appreciated, TIA!

---

### Post by astralsin on 2007-09-04
what resolution is your main desktop running? the default XP install should run at 640x480 and max out at 800x600 unless you install the guest additions.

---

### Post by ubukool on 2007-09-04
Hi Astralsin,

1280x800 for Ubuntu
1024x768 for XP

I find that when I reduce the resolution for XP, the desktop area for XP gets smaller, but all around, filling the whole screen apart from the toolbar at the top, it's black.

I tried to do a screenshot but it didn't seem to work.

Thanks for replying!

---

### Post by ubukool on 2007-09-06
Hi everyone,

I've solved the problem and want to post a solution so that if anyone else has this problem they can solve it.

The guest machine (Windows XP)  was starting in fullscreen mode for some strange reason, which I didn't know about.  You can toggle between fullscreen and windowed mode with the command HOST F where HOST is the key you use to toggle between guest and host actions (mine is F2, but I think the default is Right Control).

That solves the problem!

I'm not very familiar with virtualbox so I've had to do quite a bit of digging with google to find out about it.  I hope this helps someone.

---

### Post by mustansir on 2008-01-21
> **ubukool said:**
> Hi everyone,

I've solved the problem and want to post a solution so that if anyone else has this problem they can solve it.

The guest machine (Windows XP)  was starting in fullscreen mode for some strange reason, which I didn't know about.  You can toggle between fullscreen and windowed mode with the command HOST F where HOST is the key you use to toggle between guest and host actions (mine is F2, but I think the default is Right Control).

That solves the problem!

I'm not very familiar with virtualbox so I've had to do quite a bit of digging with google to find out about it.  I hope this helps someone.

UBUKOOL - Thanks a lot for posting this fix, I spent hours searching for the key combo's to fix this, till I found your post, and it worked. Thanks a lot.

Host: Gutsy Guest:Winxp

---

