---
title: "Black screen problem in Compiz fusion but not Beryl"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by sinfony on 2007-07-05
So I ran into the dreaded black window bug using Compiz Fusion, and after trying a bunch of xorg voodoo and other fixes, I can't get it to go away.  However, I have no such problems when I use Beryl.  Has anybody else run into this problem, or am I doing something wrong?  I've followed the installation directions precisely and, black window bug aside, Compiz Fusion works fine.

---

### Post by Alex&amp;Linux on 2007-07-05
Hey Sinfony

Beryl for me was great after I fixed the Nvidia bug, and I had just installed Fusion to find that it indeed returned to haunt me.

Unfortunately, the remedy I have been using is only temporary, but I'll offer it up.

It seems to me that upon experiencing the bug, if you re-execute Fusion, it corrects the error, and prevents further black screen issues for the session (in my brief experience)

If you wanna try , just "alt f2" and "compiz --replace" it up!

---

### Post by Alex&amp;Linux on 2007-07-05
Still sucks though!
I will continue searching for a solution!

Do you know if there is a way to change the rendering path?

---

### Post by sinfony on 2007-07-06
I'm wondering the same thing.  I've been using "Force AIGLX" in Beryl to stave off black screen problems, but I can't find any such option in Fusion.

---

### Post by Alex&amp;Linux on 2007-07-10
Check this out:

[http://www.nvnews.net/vbulletin/showthread.php?t=77030](http://www.nvnews.net/vbulletin/showthread.php?t=77030)

As far as I can tell, should be problem solved, however, I'm having trouble installing the updated driver.

---

### Post by Alex&amp;Linux on 2007-07-20
Just an update for those who may stumble upon this old thread:

The new nvidia driver (for newer cards) seemed to help me, but since I only have 128MB shared, there are still some black screens.

To solve the problem, offload the rendering responsibility to your processors by executing compiz with the following:

```
compiz --replace --indirect-rendering
```

Performance seems to be pretty great, and no black windows!

---

