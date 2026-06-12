---
title: "Keyboard shortcuts stopped working with jaunty"
date: 2009-04-29
forum: General Help
---

### Post by funkyFlash on 2009-04-29
Hey all.

I LOVE Jaunty.  It fixed quite a few of my outstanding issues (including two finger scroll on my MBP, thank god).

One issue that appeared is that none of my key shortcuts seem to work in compiz.  I have apple(super)-t mapped to terminal, and the usual suspects like alt-f1, alt-f2, and so on.  None of those work if I'm'a'compiz'n, but if I switch back to lame-o metacity, they work.

Thoughts?  Concerns?  Your mom jokes?

Thanks in advance.

---

### Post by mirzmaster on 2009-04-30
I am actually experiencing a similar problem, however mine is a bit stranger.  In my case, the keyboard shortcuts work fine at first... but then after a couple of hours of usage, they stop working.

My workaround is to disable desktop effects and then re-enable them.

Is anyone else sharing this experience?

---

### Post by mirzmaster on 2009-04-30
> **funkyFlash said:**
> One issue that appeared is that none of my key shortcuts seem to work in compiz.  I have apple(super)-t mapped to terminal, and the usual suspects like alt-f1, alt-f2, and so on.  None of those work if I'm'a'compiz'n, but if I switch back to lame-o metacity, they work.

funkyFlash, I think this might help you out:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/328679/comments/3](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/328679/comments/3)

The commentor suggests that enabling the "Gnome Compatibility" compiz plugin will solve the problem you're experiencing.

Try that out and let us know if it worked!

---

### Post by rohit2412 on 2009-04-30
i too had a similar problem...
but what i did was to remove the .gnome .gnome2 .gconf .gconfd folders

they were again created(default.....compiz was turned off too).....but now every shortcut is working

---

### Post by mirzmaster on 2009-04-30
> **rohit2412 said:**
> i too had a similar problem...
but what i did was to remove the .gnome .gnome2 .gconf .gconfd folders

they were again created(default.....compiz was turned off too).....but now every shortcut is working

But does this address the root cause, or is it a workaround?  It sounds like a workaround since you've lost the ability to use compiz.

Next time I lose my keyboard shortcuts, I'll try the advice in the following post:

[http://ubuntuforums.org/showpost.php?p=1890567&postcount=2](http://ubuntuforums.org/showpost.php?p=1890567&postcount=2)

***Edit:**  The suggestion at the above link didn't work.  :(*

---

### Post by funkyFlash on 2009-05-01
Fantastic.  Gnome compatibility did the trick.  Thank you much!

---

### Post by mirzmaster on 2009-05-01
> **funkyFlash said:**
> Fantastic.  Gnome compatibility did the trick.  Thank you much!

Awesome.  You should mark this thread solved then.  :)  I can always open a new thread for my problem.

---

