---
title: "need to switch compiz on and off upon startup"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by darktreb on 2008-02-07
I'm having a strange "problem" (not sure it's even right to call it that) where I want to use Compiz on medium settings, but upon startup, when I try to drag my mouse on the desktop, the box created by dragging lags far behind my actual mouse pointer. However, upon switching compiz off and then back on again, this is no longer the case. I'm not too well-versed on what exactly compiz runs or is doing upon startup, and clearly compiz works fine overall (even if I don't switch it off and on, everything runs smoothly except for the mouse dragging as far as I can tell). Any thoughts to what the problem could be?

---

### Post by pieisgood4589 on 2008-02-07
I had this happen to me- I just reset the xorg files, and re-installed my drivers. Yup...:guitar:

---

### Post by darktreb on 2008-02-07
Hmm, tried that but still the same thing remains.

---

### Post by nilarimogard on 2008-02-07
You can try installing compiz-switch, and maybe running it on startup twice... the first time normal, and the second time with a delay so it switches off and on.

This is to install it:
sudo apt-get install compiz-switch

Then make a new file and name it compizonoff.sh in which you copy/paste this:
> #!/bin/bash
sleep 10 && compiz-switch ;

and run this in a terminal window: chmod +x compizonoff.sh
Then just add /bla/whatever/compizonoff.sh to your startup. Remeber that you need to add also normal compiz-switch to startup, so it turns it off the first time, and then on.
I haven't tried it, but in theory it should work :)

---

