---
title: "Broken mouse"
date: 2012-02-28
forum: Desktop Environments
---

### Post by Mr.Pytagoras on 2012-02-28
Hi

Well, the problem is that my mouse is broken and when I click the left button it generates 2 mouse clicks, so until I buy a new mouse I need to somehow temporarily fix it.

My idea is to set some kind of limit between mouse clicks, that when you click the mouse then you will have to wait let say  0.2sec before you can click it again and every mouse clicks generated before passing those 0.2sec will be ignored

:)

Any ideas how to do it (set up it) in ubuntu 11.04?

Thanks

---

### Post by MG&amp;TL on 2012-02-28
In my understanding, not without some serious messing around. I would think it would be considerably easier to use the keyboard to click, as shown here: [https://help.ubuntu.com/11.04/ubuntu-help/mouse-mousekeys.html. ]("https://help.ubuntu.com/11.04/ubuntu-help/mouse-mousekeys.html")

Hope this helps. And sorry about your mouse, I think I would be lost getting used to a new keyboard (don't use the mouse much).
[]("https://help.ubuntu.com/11.04/ubuntu-help/mouse-mousekeys.html")

---

### Post by Mr.Pytagoras on 2012-02-28
Thanks for your post, however I already know how to use keyboard to emulate mouse but that is not what I want to do

I've managed to fix my mouse problem with a screwdriver and a sandpaper :)
  
However, I'm still curious how to do it as I described in my first post

> **MG&TL said:**
> In my understanding, not without some serious messing around. I would think it would be considerably easier to use the keyboard to click, as shown here: [https://help.ubuntu.com/11.04/ubuntu-help/mouse-mousekeys.html. ]("https://help.ubuntu.com/11.04/ubuntu-help/mouse-mousekeys.html")

Hope this helps. And sorry about your mouse, I think I would be lost getting used to a new keyboard (don't use the mouse much).



MG&TL could you please post what did you mean by serious messing around?

---

### Post by MG&amp;TL on 2012-02-29
Cool. Finding the source of the problem is usually the best idea. :)

Well, as I understand it (no expert), the kernel modules for the various types of mice feed data form the hardware to the X.org server (which handles display windows, drag and drop, and various clicky events), which then feeds signals to applications. Since to interrupt that process, you would have to mess about with kernel modules (not a good idea), mess about with the X server (still not a good idea), or do something to the signals (v. complicated). I'm not entirely sure how the mouse settings work, presumably there is a configuration file for mice somewhere.

---

### Post by Mr.Pytagoras on 2012-02-29
There are apps that can capture key or mouse events, wouldn't be possible to code some kind of a mask (let say using glib or gtk) that would be always on top and every mouse event would have to go through that mask?

I'm getting better in programing every day and I have already done some apps for myself, so maybe I will try to do something like that, however messing with X's code or even kernel's code is i think beyond my current skills

---

### Post by MG&amp;TL on 2012-02-29
> **Mr.Pytagoras said:**
> There are apps that can capture key or mouse events, wouldn't be possible to code some kind of a mask (let say using glib or gtk) that would be always on top and every mouse event would have to go through that mask?

I'm getting better in programing every day and I have already done some apps for myself, so maybe I will try to do something like that, however messing with X's code or even kernel's code is i think beyond my current skills

You should give it a go. Xserver #2 much? :P

Hope I answered your question okay.

---

