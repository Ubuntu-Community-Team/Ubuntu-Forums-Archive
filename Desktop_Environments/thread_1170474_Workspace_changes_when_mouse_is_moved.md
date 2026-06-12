---
title: "Workspace changes when mouse is moved"
date: 2009-05-26
forum: Desktop Environments
---

### Post by jeffrla on 2009-05-26
Hi all,

I am having an issue that I honestly cannot figure out why it is happening.

I have Ubuntu 8.10 installed with all the default settings (clean install).

I have the 2 default workspaces and periodically when I move the mouse, it changes workspaces.  This has become REALLY annoying.  I found a workaround by just having 1 workspace, but I like the idea of multiple workspaces, I just wish it would STOP changing workspaces when I move the mouse.

I have tried to identify if it is some way I am moving the mouse, but nothing seems to fit.

Can anyone help me understand why the workspaces change?

Thanks,

Jeff

---

### Post by Boondoklife on 2009-05-26
Hey I had a similar issue, but it was that I was hitting a button on the mouse when I used it that enables the scrolling of the screens.

Only solution I found was to just simply not hit the button =).

But check in ccsm (CompizConfig Settings Manager) and check under view port, you can change the behavior there.

---

### Post by jeffrla on 2009-05-26
Thanks for the info.  One things I should add is that it only seems to change the workspaces when I use the touchpad on the laptop.  Does not seem to happen if I have an external mouse attached.

Thanks again,

Jeff

---

### Post by Boondoklife on 2009-05-26
> **jeffrla said:**
> Thanks for the info.  One things I should add is that it only seems to change the workspaces when I use the touchpad on the laptop.  Does not seem to happen if I have an external mouse attached.

Thanks again,

Jeff

You might be hitting the scroll section when the mouse is over the desktop. This will cause it to change viewports.

---

### Post by pricetech on 2009-05-26
I haven't noticed this in Jaunty, but did in Hardy.  It seems if my cursor is focused on "nothing" the workspace would switch when I scrolled.  I got used to it pretty quickly and ignored it after that.

---

### Post by jeffrla on 2009-05-26
Hi all,

I do not know where the scroll space is.  I will need to research that now.

Thanks,

Jeff

---

### Post by Bearly Able on 2009-05-26
And all this time I thought it was just me!

I've had the same problem with Hardy on my Lenovo laptop, and after months of trying to figure out what was causing the workspace to switch, I gave up in frustration and deleted one of the workspaces.  I've since acquired an external mouse; I'll give it a go and see if the problem still occurs with that.

---

### Post by mcduck on 2009-05-26
It's simple, scrolling with mouse wheel while cursor is over desktop (instead of any program window) will scroll between virtual desktops.

That's hardly a problem for anybody when using normal mouse, but when using a touchpad it's of course pretty easy to accidentally touch the scrolling area of the touchpad. In that case you can disable the feature with CompizConfig Settings Manager.

---

### Post by xXeHPiCXx on 2009-05-26
I have that too.Its not a problem.You have a laptop im guessing?ok on every laptop on the right side of the touch pad if you slide up or down the workspaces switch.If you accidentally switch the work spaces.press control+alt and then press left or right.

---

### Post by mcduck on 2009-05-27
If you want to disable the feature, the way to do that s to open CompizConfig Settings manager (install it if you haven't done that already). Go to Viewport Switcher-plugin and on the "Desktop-based Viewport Switching"-tab remove the shortcuts.

---

### Post by dj722000 on 2009-05-30
I seen this in UBUNTU 8.10. Then I quickly realised I was just lightly tapping the wheel on the mouse when I moved the cursor. I also noted that sometimes the wheel on the mouse would gently stick in between the two notches, then a quick jerk of the mouse it would roll into place and scroll my screen. I bought a new mouse and havent had the problem since.  :popcorn:

---

