---
title: "Workspace Switcher: open programs getting WARPED!"
date: 2011-10-04
forum: Desktop Environments
---

### Post by kingtz on 2011-10-04
OS: 11.04 x64; ATI proprietory drivers, Compiz installed
PC: i7720QM; ATI HD5870M; 8GB 1333 RAM

As you can see in the screen shots below, open windows are getting severely warped when I move my cursor around in workspace switcher. For example, say I have Chrome maxed out in workspace 1 and my music player maxed out in workspace 3. If I go to the workspace switcher mode (SUPER+S) and try to move my cursor over from one workspace to another, whatever program that I have maxed in the first workspace will warp and distort to follow my mouse cursor. The program within the workspace literally distorts and moves around with my cursor.

I've noticed that this generally happens when I have the open program maxed out in the workspace; this doesn't happen when I have the same program open, but not maxed out. I can reproduce this bug/problem fairly consistently. 

I have a hunch that this has to do with some of my Compiz settings either clashing with each other or bugging out, but I'm not sure which settings specifically. Can someone who's familiar with this issue or even with Compiz walk me through this? 

Thanks in advance.

---

### Post by stinkeye on 2011-10-04
In ccsm > desktop > expo
under the behaviour tab, try enabling **immediate moves**.
This disables wobbly windows when in expo mode.

---

### Post by kingtz on 2011-10-05
> **stinkeye said:**
> In ccsm > desktop > expo
under the behaviour tab, try enabling **immediate moves**.
This disables wobbly windows when in expo mode.

I've been testing this for the last day or so. The problem seems to still be occurring. I've even tested on a fresh boot, and it still happens.

Are there any other Compiz settings that I can play around with? Would this issue have anything to do with the "stickiness" of the windows and how can I adjust this?

---

### Post by stinkeye on 2011-10-05
> **kingtz said:**
> I've been testing this for the last day or so. The problem seems to still be occurring. I've even tested on a fresh boot, and it still happens.

Are there any other Compiz settings that I can play around with? Would this issue have anything to do with the "stickiness" of the windows and how can I adjust this?

Could try enabling mipmaps in the expo plugin but I think it may be an ATI
driver issue as I don't have the problem with my nvidia card.

Also try disabling the maximize effect in the wobbly windows plugin.

---

### Post by Copper Bezel on 2011-10-05
I've had this problem as well. I don't have anything to add except that for me, it's very unpredictable, and it's quite bizarre to see the windows stuck that way and, further, since the window is still responsive in this state, which clicks will be redirected to match the warp and which won't.

---

### Post by Krytarik on 2011-10-05
Have you already tried this!?:

[http://www.tuxgarage.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://www.tuxgarage.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

Hope that works!

---

### Post by kingtz on 2011-10-06
> **Krytarik said:**
> Have you already tried this!?:

[http://www.tuxgarage.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://www.tuxgarage.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

Hope that works!

Yeah, that feature has always been disabled for me.







UPDATE: I disabled the curvature of the Workspace Switcher (now it's the default flat style). So far, I haven't been able to reproduce the issue. I'll give it another day of testing this out before I can confirm, and maybe others with this issue can help me confirm this.

---

### Post by Copper Bezel on 2011-10-06
I've seen the problem without the curvature enabled. It wasn't a consistent problem, however, and I couldn't figure out what triggered it.

[[img]http://dl.dropbox.com/u/17749392/Screenshots/111002/Screenshot-5.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/111002/Screenshot-5%20%28copy%29.png)

I don't think it's an ATI problem, because I'm on Intel.

---

### Post by kingtz on 2011-10-07
> **Copper Bezel said:**
> 

I don't think it's an ATI problem, because I'm on Intel.

You mean Nvidia?

---

### Post by Copper Bezel on 2011-10-07
No. Which part? You're on ATI, correct? I'm on an integrated Intel chip and can reproduce the problem.

---

### Post by kingtz on 2011-10-10
> **Copper Bezel said:**
> No. Which part? You're on ATI, correct? I'm on an integrated Intel chip and can reproduce the problem.

Sorry, I totally forgot about integrated graphics. 

UPDATE: so far so good. Haven't had any of the stickiness or warping since switching over to the flat switcher.

---

### Post by kingtz on 2011-10-18
UPDATE:

I think I narrowed it down! Hopefully other people with this issue can help me test this out.

I have a strong feeling now that the issue is caused by Wobbly Windows. Earlier today, I was playing around with a Linux Mint Live CD and messing around with the Compiz settings on it. Everything was fine until I turned on Wobbly Windows. Right after I did that, as soon as I switched to the Workspace Switcher, I noticed the same issue with the mouse cursor sticking to the windows and warping and distorting stuff. Problem went away right after I turned off Wobbly Windows.

What do you guys think?

---

### Post by Copper Bezel on 2011-10-18
I kinda thought we were assuming that. = ) The deformation looks like the window is being stretched based on the cursor position. It's definitely caused by Wobbly Windows, but I doubt if there's an easy fix without deactivating the plugin. (I don't normally use it.)

---

