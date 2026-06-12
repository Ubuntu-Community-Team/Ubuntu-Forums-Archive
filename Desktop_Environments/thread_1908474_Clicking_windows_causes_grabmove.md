---
title: "Clicking windows causes grab/move"
date: 2012-01-13
forum: Desktop Environments
---

### Post by Apewall on 2012-01-13
Clicking in the top header area of a non focused window causes your mouse to grab the window and then move it, as if you were using ALT+Click as is default in XFCE.

I'm not sure this is even an intended feature, but it is very annoying, especially on programs like Chromium where there is no border drawn by the window manager for you to click.

Anyone know how to disable this, or is this a bug, I've dug in the XFCE documentation but found NOTHING about it.

---

### Post by wkrekik on 2012-01-13
Strange.
Have you tried to delete some configuration folders (~/.cache ~/.config/Thunar ~/.config/xfce4 ~/.config/xfce4-session). Of course back-up them before deleting.

---

### Post by Apewall on 2012-01-13
> **wkrekik said:**
> Strange.
Have you tried to delete some configuration folders (~/.cache ~/.config/Thunar ~/.config/xfce4 ~/.config/xfce4-session). Of course back-up them before deleting.

Yes, this seems to be the default behavior at least on xubuntu 11.10

It also does this on 3 separate machines.  I forgot to note that this only occurs on windows that do not currently have focus, edited to reflect this in my original post.

---

### Post by Krovas on 2012-05-03
Does anybody know a cure for this behavior? It is intensely irritating.

---

### Post by malv83 on 2012-05-20
I have this problem as well with Xubuntu 12.04.

---

### Post by rai4shu2 on 2012-05-20
Could you describe what the problem is in more detail? I'm having some difficulty understanding what's going wrong precisely.

---

### Post by GrandTheft on 2012-05-23
I am having the same problem, too. 

Description: (example) resize window to fill 90% of screen height, 50% width, click on middle of window, window jumps to the lower right corner of the screen (with mouse pointer attached), sometimes moving it to adjacent desktop. 

Dunno what caused it, didnt happen before. :confused:

best regards,
gt

---

### Post by anaconda on 2012-05-23
i am having this problem too.

Extremely annoying with touchpad on my asus eeepc.
It is sometimes difficult to release the grapped window.

dont really know what I do when it happens.

anyone have a fix?

---

### Post by rai4shu2 on 2012-05-23
I don't think anyone can fix what they can't observe. Sorry.

Record it and post it on Youtube if you can't describe it better than that.

---

### Post by jadtech on 2012-05-23
i cant replicate this what so ever on this HP g6 running 12.04 wireless mouse or touch pad

---

### Post by morgengenuss on 2012-05-31
Unfortunately I'm aware of this problem. I thought I fixed it when I switched off window-moving by grabbing the toolbar in Greybird. I guess I'll have to investigate this further.

Please file a bug on launchpad for it, ideally against shimmer-themes so we can track it properly there.

---

### Post by neptvn on 2012-06-02
I've managed to reproduce this problem (just gedit) and recorded it for those who don't understand what's happening.

[http://www.youtube.com/watch?v=Ir2IDxFKBFA](http://www.youtube.com/watch?v=Ir2IDxFKBFA)

From description:

         When I click and release the header of  the window (not the title bar, but below it == same height as the menu)  and afterwards click and release anywhere inside the window the cursor  grabs the window and moves it at the slightest mouse movement without  holding any button.

---

### Post by jejeman on 2012-06-14
> When I click and release the header of the window (not the title bar, but below it == same height as the menu) and afterwards click and release anywhere inside the window the cursor grabs the window and moves it at the slightest mouse movement without holding any button. Exactly, same here.
Ubuntu Studio 12.04. Xfce.

Where is the bug report?

---

### Post by malv83 on 2012-06-16
> **jejeman said:**
> Exactly, same here.
Ubuntu Studio 12.04. Xfce.

Where is the bug report?


The reported the bug here since it seems to be a GTK3+ app related bug

[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1001936](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1001936)

Be sure to mark that you're affected so they hopefully fix it soon. It's an intensely annoying rage-inducing bug.

---

### Post by rai4shu2 on 2012-06-17
Interesting. It looks like we're seeing two different issues:

#1: Clicking anywhere in the menu-box causes the window to drag the same as if you had clicked on the title portion of the window.

#2: GTK 3 apps move to the lower right corner of the screen if you click drag on the menu box, then click on another area in the client portion of the window (the window moves immediately after you begin the first mouse move after you click in the blank area of the window).

---

### Post by GrandTheft on 2012-09-07
anyone found a fix for this in the meantime?

---

### Post by Elfy on 2012-09-07
Are you completely updated - there was an apparent fix released a while back.

[https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/1001936](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/1001936)

---

### Post by neptvn on 2012-09-10
I am completely updated and I'm still having the bug, using Xubuntu 12.04 with Xfce 4.10 from [this PPA]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10"). Am I missing something? Should I apply [the patch from here]("https://launchpad.net/ubuntu/+source/xfwm4/4.10.0-2ubuntu1") myself? If so, could someone help me out?

Thanks.

---

### Post by Ovocean on 2012-11-14
> **neptvn said:**
> I am completely updated and I'm still having the bug, using Xubuntu 12.04 with Xfce 4.10 from [this PPA]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10"). Am I missing something? Should I apply [the patch from here]("https://launchpad.net/ubuntu/+source/xfwm4/4.10.0-2ubuntu1") myself? If so, could someone help me out?

Thanks.Coming late but since your question was unanswered: no you're not missing anything, the version in the PPA isn't patched. If you really can't wait you can ask the PPA maintainer to update xfwm (or compile it yourself =).

---

