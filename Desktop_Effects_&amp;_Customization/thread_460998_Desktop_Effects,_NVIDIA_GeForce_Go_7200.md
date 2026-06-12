---
title: "Desktop Effects, NVIDIA GeForce Go 7200"
date: 2007-06-01
forum: Desktop Effects &amp; Customization
---

### Post by szabodabo on 2007-06-01
Hi all,

I have a new HP dv2000 laptop that runs Ubuntu beautifully.  But with one problem.

I try to use the Desktop Effects in Feisty, and it works, as I have the restricted NVIDIA drivers, but after a while, the windows start opening as frames with black fill.  The windows open, but all I see is the title bar and the side frames, but inside the window is all black.

I should note that this doesn't happen when Desktop Effects isn't enabled.
And I had Beryl on 6.10, it used to do it also.

Please help!
Thanks!

---

### Post by simplyw00x on 2007-06-05
I also experience this problem; and with no beryl-manager, the workaround of changin the render path is useless.

---

### Post by chriswyatt on 2007-06-05
Yes, there are workarounds on Beryl's official forums.  I found that these helped but didn't completely remove the problem, but they definitely did let me run more windows at the same time.  It's annoying because my video card has 128 megs of memory not to mention it's AGP, so in terms of hardware it should be able to handle it, oh well.  Give it time and I think these problems will be ironed out.

Personally, I value performance over the bells and whistles of Beryl, so I've got it disabled at the moment, but I had some fun fiddling about with it.

---

### Post by PsychedelicReaction on 2007-06-07
i have the same card and this worked for me:

manually edit compiz startup script with

sudo gedit /usr/bin/compiz

then in the COMPIZ_OPTION line put "--replace --indirect-rendering gconf &"

restart your x server and should work

---

