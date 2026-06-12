---
title: "Window Scrolling is Too Slow When Using Beryl"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by hermesrules on 2007-04-30
Hi,

I have an older laptop machine (AMD Athlon XP 2200+) with an integrated ATI Mobilty U1 video card and 64 MB of shared video RAM (taken from a total of 1 GB of RAM). Until recently, using any kinds of desktop effects was not possible on this machine (I mean it was way tooo slow to be usable).

What works for me is the open source ati drivers with AIGLX (no XGL) and Beryl (latest version). However the only thing slow now is scrolling inside windows. A full screen web site is ugly to watch scroll up or down. Remarkably, that does not happen on many LiveCDs I've tried with the desktop effects on, and I can't see what I have done differently.

Perhaps someone could suggest some options I need to tinker to make scrolling smoother and as fast as before.

I am using KDE 3.5.6.

Thanks in advance for any help!

---

### Post by alphane on 2007-04-30
I think it's something to do with the way Beryl handles the redrawing.  I know when I used Beryl before (don't at the moment, it caused issues with video playback) that Scrolling and Window resizing were both really quite awful, and this is using a fairly powerful X800 Pro.

The window resizing I fixed by letting Beryl handle that, but the scrolling was pants as ever.  I don't know whether there's a fix, but the point of my post is to say that if you can use all the other effects fine, then chances are that it's not your graphics that are letting you down!

---

### Post by eentonig on 2007-04-30
Probably you have too much high spu intensive beryl effects running. I needed to disable a few features as well, because otherwise beryl was using to much cpu to be workable.

It's not because you can run it, that your pc is up to the task.

---

### Post by hermesrules on 2007-04-30
> **eentonig said:**
> Probably you have too much high spu intensive beryl effects running. I needed to disable a few features as well, because otherwise beryl was using to much cpu to be workable.

It's not because you can run it, that your pc is up to the task.

You are absolutely right the PC is not really up to the task. On another computer with an even older NVIDIA card, there were no such issues (using the proprietary nvidia driver), and it was working like a blast! But I still need to use my machine...

As with the effects and CPU usage... In fact, I notice CPU usage increase (up to about 70%) when I scroll intensively inside a Konqueror window. Minimizing and maximizing (magic lamp) do not seem to affect CPU usage.

What features are you suggesting I disable, if that were to improve scrolling inside windows?

Thanks!

---

### Post by hermesrules on 2007-04-30
> **alphane said:**
> The window resizing I fixed by letting Beryl handle that, but the scrolling was pants as ever.  I don't know whether there's a fix, but the point of my post is to say that if you can use all the other effects fine, then chances are that it's not your graphics that are letting you down!

That's the kind of logic I have too! Moreover, I have proof that it does not always have to be slow - for example, using PCLOS LiveCD (latest beta, I think), lets me configure desktop effects in less than a minute, and then I don't notice any lagging whatsoever. So it's probably some settings I need to tinker. Perhaps versions of beryl are not all that different, as I believe I am using the very latest (which is probably not a good idea, but being the enthusiast that I am...).

I don't quite understand what you mean - to let beryl handle resizing. In fact, I had it set to using colored rectangle instad of painting or stretching the contents of the window being resized. Constant painting proved to be quite slow (sort of made me unwilling to resize anything), and stretching is ugly, perhaps it is just a proof of concept, and I see no practical value in it. So I assume I have let Beryl handle resizing too...

I am glad to see how much development Beryl has undergone in the past few months. This is not my first attempt at it, however, it is the most successful one to date. Previous attempts have seen Beryl crash all too often, the white screen of death, etc. Now I don't even have issues with video playback. There is no difference in performance in video playback with or without Beryl.

Cheers!

---

