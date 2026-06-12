---
title: "Undesired transparency of active windows"
date: 2009-01-14
forum: Desktop Environments
---

### Post by joshis on 2009-01-14
Hi, I am using Ubuntu 8.10 with Compiz and I have following problem (that I haven't found anywhere on the forums):

Sometimes, a window decoration of an active window is messed up
- with Mist: decorations become 100% transparent, so that I can see only a white border around it and the text in the window title bar, but the background seems to be gone
- with default Ubuntu theme: decorations become grey and letters are somehow transparent.

I had this issue all the time when using default Ubuntu theme (attaching screenshots of the messed up decorations with default theme). Now I am using Mist and the issue happens much less often, reproducibility is random, but it still happens.

Is there anyone experiencing the problem or anyone who knows what can be wrong and how to fix it?

If you need more info about my system, please ask me for it (I don't know where to start)...

---

### Post by 5BallJuggler on 2009-01-14
What happens if you turn off "Window Decoration" in compiz?

---

### Post by joshis on 2009-01-14
> **5BallJuggler said:**
> What happens if you turn off "Window Decoration" in compiz?

window decorations disappear (there are no decorations, I have to turn it back on)

---

### Post by 5BallJuggler on 2009-01-14
Try changing the setting in Compiz Windows Decorator to these, see what happens then.

---

### Post by joshis on 2009-01-14
> **5BallJuggler said:**
> Try changing the setting in Compiz Windows Decorator to these, see what happens then.

Nothing special actually - the problem still persists:(... I just have some shadow under the window that I didn't have there before (and which I will get rid of). But thanks for suggestion anyway.

Any other suggestions? :( Should I provide some information here (xorg.conf, etc.)?

There is no problem when I turn the compiz off, so this might be a way to go...

OT: Sorry for the late reply, I was on the test of computational complexity, it was... well, not so complex as I expected;)...

---

### Post by joshis on 2009-01-14
Maybe this should have gone to "Desktop Effects & Customization" category... ??

---

### Post by joshis on 2009-01-14
OK, I have found it here on the forums:

[http://ubuntuforums.org/showthread.php?t=1004901&highlight=window+decorations](http://ubuntuforums.org/showthread.php?t=1004901&highlight=window+decorations)

Using Emerald helps too - I will probably go this way, the forum above suggests using 32bit driver (I am on 64bits)...

Thank you for your help!

---

### Post by TheOrangePeanut on 2009-01-14
Compiz always did that to me too.  I never figured out why.  Kwin didn't do that, and I like KDE4 better than Gnome anyhow, so it just made sense to switch..

---

### Post by joshis on 2009-01-14
> **TheOrangePeanut said:**
> Compiz always did that to me too.  I never figured out why.  Kwin didn't do that, and I like KDE4 better than Gnome anyhow, so it just made sense to switch..

Well, it is also one way to go, except I personally don't like KDE4 (KDE3 was slightly better, IMO).

It's mainly because the desktop is too "reinvented" in KDE4. It is more a place for the widgets, and I don't like it that way - I like to have some temporary files (just downloaded, etc.) on the desktop so that I can manipulate them. I don't want to use a widget that reserves some portion of the screen for the purpose. This is also problem in my philosophy, I guess...

KDE4 is also too bold and everything takes too much space (+ too much work to set it up properly). I like simpler and lighter themes...

I am playing with Emerald right now, it seems to work pretty well, but there are no themes I really like (I have a "Vista" look&feel now, bot it will go away... yes... yes, it will...)

---

