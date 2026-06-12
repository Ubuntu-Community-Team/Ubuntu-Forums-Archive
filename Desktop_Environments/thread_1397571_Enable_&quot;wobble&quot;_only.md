---
title: "Enable &quot;wobble&quot; only"
date: 2010-02-03
forum: Desktop Environments
---

### Post by flyver on 2010-02-03
I'm fairly new to Linux, but I've worked quite a bit lately with this operating system, mostly trying Ubuntu, Xubuntu and Linux Mint.

I decided to for Xubuntu 9.10 on my notebook. I love the default Albatross theme and the icons and the general look, the only thing I have changed is "Compositor" (to enable shadows and opacity of windows decorations).

There is _one_ more thing I would like to add, and that's the wobble effect. It seems I can only get this with Compiz, however Compiz changes my windows decorations just a little bit, but still I would like Compiz to leave that alone!

Is there any way I can activate only the wobble effect?

Thank you!

---

### Post by flyver on 2010-02-03
I would like to add that I have tried installing Ubuntu and then installing the XFCE environment, hoping I would then have access to the seemingly built-in Compiz "visual effects" tab. Seemed like a logical train of thought...

Also, although I only need "wobble" I don't mind having other visual effects. What I can't figure out is how to use Compiz without it interfering with the XFCE window manager, that is, my preferred settings regarding window titles, borders, icons... I love Albatross.

---

### Post by mcduck on 2010-02-03
> **flyver said:**
> I'm fairly new to Linux, but I've worked quite a bit lately with this operating system, mostly trying Ubuntu, Xubuntu and Linux Mint.

I decided to for Xubuntu 9.10 on my notebook. I love the default Albatross theme and the icons and the general look, the only thing I have changed is "Compositor" (to enable shadows and opacity of windows decorations).

There is _one_ more thing I would like to add, and that's the wobble effect. It seems I can only get this with Compiz, however Compiz changes my windows decorations just a little bit, but still I would like Compiz to leave that alone!

Is there any way I can activate only the wobble effect?

Thank you!

I don't think XFWM's comositor has such an effect, so your only option is to use Compiz. Sadly, Compiz doesn't have any decorator plugin that would use XFWM themes so there is no way to keep those decorationss you are now using with XFWM. Your only option is to try to find a Metacity (or Emerald) theme that would look like your current XFWM theme..

(and no, Compiz can't just leave the decorations alone. It's a window manager, just like XFWM is, so if you run Compiz you can't have XFWM running at the same time. Two programs trying to both manage your windows at the same time simply wouldn't work)

---

### Post by Simian Man on 2010-02-03
What about using the Fusion Icon program?  I know it lets you choose the window manager and window decorator separately, but I don't know if it relies on special compiz plugins for each WM to make that work.  Might be worth a try at any rate.

---

### Post by mcduck on 2010-02-03
> **Simian Man said:**
> What about using the Fusion Icon program?  I know it lets you choose the window manager and window decorator separately, but I don't know if it relies on special compiz plugins for each WM to make that work.  Might be worth a try at any rate.

That won't help.

The thing is that XFWM is a window manager, and Compiz is a window manager. You simply can't run two window managers at the same time.

The things called "window decorators" are just plugins for Compiz, you must run Compiz to use them (and you must use one of them to get any window decorations with Compiz). XFWM on the other hand is a full-blown window manager, not just a decorator plugin..

(and no, there are no such things as compiz plugins for window managers. Compiz is the only window manager that uses Compiz plugins...)

---

### Post by Simian Man on 2010-02-03
> **mcduck said:**
> The thing is that XFWM is a window manager, and Compiz is a window manager. You simply can't run two window managers at the same time.

The things called "window decorators" are just plugins for Compiz, you must run Compiz to use them (and you must use one of them to get any window decorations with Compiz). XFWM on the other hand is a full-blown window manager, not just a decorator plugin..

(and no, there are no such things as compiz plugins for window managers. Compiz is the only window manager that uses Compiz plugins...)

I know all of that.  Compiz has the ability to use metacity, emerald or kwin themes for the window decorations.  I was wondering if it could do the same for xfwm, but [this page]("http://wiki.compiz.org/Plugins/Decoration") suggests that the three I mentioned are the only ones that are supported now.

---

### Post by flyver on 2010-02-04
Thanks for answering.

What about [this]("http://shimmerproject.org/projects/albatross/")? Would this enable me to install Ubuntu, and then add this theme?

Of course, I wanted to use Xubuntu considering it should be faster (although I'm not that sure that is true?)...

Anyway, it seems I better find another theme to like.

---

### Post by mcduck on 2010-02-05
> **flyver said:**
> Thanks for answering.

What about [this]("http://shimmerproject.org/projects/albatross/")? Would this enable me to install Ubuntu, and then add this theme?

Of course, I wanted to use Xubuntu considering it should be faster (although I'm not that sure that is true?)...

Anyway, it seems I better find another theme to like.

That seems to be just a GTK + XFWM theme, so the window borders only work if you use XFWM as your window manager.

The GTK theme of course will work in any environment.

---

### Post by flyver on 2010-02-05
OK well... Thanks anyway.

---

