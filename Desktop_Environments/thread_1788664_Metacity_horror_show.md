---
title: "Metacity horror show"
date: 2011-06-23
forum: Desktop Environments
---

### Post by rau on 2011-06-23
Welcome to my reality. If I use Compiz, I get horrible performance (in reality, not any worse than anyone else, I just think Compiz sucks for performance and refuse to use it), if I use Metacity with composition enabled, everything is just fine... except that I get HORRIBLE OpenGL performance in windowed mode, and if I use Metacity with composition dissabled, I get THIS:

[IMG]http://s3.postimage.org/4ycsh22qh/Screenshot.jpg[/IMG]

I swear, I just can't win.

ps: HD5850 with AMD 8.84.6 drivers

---

### Post by wildmanne39 on 2011-06-23
Hi, while using compiz do this and it will most like fix your performance problem.
    Install CompizConfig Settings Manager from either the Software Center, or Synaptic.
    Click on the Composite tab, and un-check Detect refresh rate.
    Back to main menu.
    Click on the OpenGL tab.
    Uncheck Sync to Vblank.

---

### Post by rau on 2011-06-23
> **wildmanne39 said:**
> Hi, while using compiz do this and it will most like fix your performance problem.
    Install CompizConfig Settings Manager from either the Software Center, or Synaptic.
    Click on the Composite tab, and un-check Detect refresh rate.
    Back to main menu.
    Click on the OpenGL tab.
    Uncheck Sync to Vblank.

I've already done that actually, and I'm still not happy with Compiz. Moving windows around is still not as smooth as Metacity is, and with Compiz, you have to disable the showing of window contents while resizing to cover up the horrible design flaws. Compare that, to Metacity, which is always silky smooth at window resizing. I never had any Metacity issues with older versions of Ubuntu.

---

### Post by FormatSeize on 2011-06-23
> **rau said:**
> I've already done that actually, and I'm still not happy with Compiz.
Is it absolutely necessary that you run Compiz? In my experience, the only purpose Compiz has served is to spin the desktop cube (only once or twice because too many times and it will break) and have a visitor come close to saying, "cool". Beyond that, it breaks or breaks other things. 
 
My question, though, is whether or not there is a friendlier alternative to Compiz. There are days when I would enjoy those bells and whistles that it provides, but is there anything else like it?

---

### Post by rau on 2011-06-23
> **FormatSeize said:**
> Is it absolutely necessary that you run Compiz?

You apparently didn't take the time to read my post. I never said I wanted to use Compiz, I have specifically said that I dislike Compiz and refuse to use it. My problem is that Metacity wont work correctly.

---

### Post by FormatSeize on 2011-06-23
> **rau said:**
> You apparently didn't take the time to read my post. I never said I wanted to use Compiz, I have specifically said that I dislike Compiz and refuse to use it.
Fair enough. But what's the difference between "Meta City with Compositiing" and "Compiz" when they both do basically the same horror show?

---

### Post by wildmanne39 on 2011-06-23
> **rau said:**
> I've already done that actually, and I'm still not happy with Compiz. Moving windows around is still not as smooth as Metacity is, and with Compiz, you have to disable the showing of window contents while resizing to cover up the horrible design flaws. Compare that, to Metacity, which is always silky smooth at window resizing. I never had any Metacity issues with older versions of Ubuntu.Hi, are you logging in to unity or classic mode?

---

### Post by tgalati4 on 2011-06-23
Burn a Lucid LiveCD and boot off of that.  Open a terminal:

metacity --replace

And see how that works.

Ochen Horror Show

---

