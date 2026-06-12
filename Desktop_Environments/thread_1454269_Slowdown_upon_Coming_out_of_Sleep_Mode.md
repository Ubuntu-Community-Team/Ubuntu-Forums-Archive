---
title: "Slowdown upon Coming out of Sleep Mode"
date: 2010-04-14
forum: Desktop Environments
---

### Post by Xorlathor on 2010-04-14
Whenever I leave my computer, it automatically goes into some kind of low-power mode, so when I come back to it and move the mouse, it shows a login screen. However, everything is ridiculously slow after logging back into my computer and I have no idea why. Is this a common problem?

---

### Post by SnickerSnack on 2010-04-14
How long does the slowdown last?

How much swap space do you have?

You are running 10.04 right?  Which beta release, or alpha?

If you go to System>Preferences>Screensaver, you have it not lock the screen.  And/or you can change how long it takes for the computer to go to sleep in System>Preferences>PowerManagement.

---

### Post by Xorlathor on 2010-04-14
No swap space - I don't like having more partitions than I need. I have 2 GB of RAM so I didn't think I needed it...am I wrong?

I just got the updated kernel and it seems to be fixed - either way, I unchecked the lock screen option so I should be okay. Thanks!

---

### Post by Xorlathor on 2010-04-16
Okay I take that back - it's still slowing down despite disabling sleep mode. It's not a problem with sleep mode, then, but something else. Anyone have any suggestions?

---

### Post by SnickerSnack on 2010-04-16
> **Xorlathor said:**
> Okay I take that back - it's still slowing down despite disabling sleep mode. It's not a problem with sleep mode, then, but something else. Anyone have any suggestions?

When is it slowing down?  When coming out of the "low-power mode" still?

Well, maybe you need to figure out what the right name for this "low-power mode" is?  I wasn't earlier suggesting that you should adjust the unrelated "sleep" settings, I was suggesting that this "low-power mode" _was_ sleep mode.  My point was that you can set the computer to remain idle longer before going to sleep.  But, there is also "hibernate".  Try turning that off too, if there is such a setting.

Is the computer set to spin down the hard disks whenever possible?  You need to go through all of the power management settings and try them all.

How about the screensaver?  Is it set to lock the screen?  What time delay setting does it have?

---

### Post by shaka_zulu on 2010-04-16
Do you have laptop or desktop?

---

### Post by Xorlathor on 2010-04-17
> **shaka_zulu said:**
> Do you have laptop or desktop?

Laptop.

---

### Post by Xorlathor on 2010-04-17
> **SnickerSnack said:**
> When is it slowing down?  When coming out of the "low-power mode" still?

Well, maybe you need to figure out what the right name for this "low-power mode" is?  I wasn't earlier suggesting that you should adjust the unrelated "sleep" settings, I was suggesting that this "low-power mode" _was_ sleep mode.  My point was that you can set the computer to remain idle longer before going to sleep.  But, there is also "hibernate".  Try turning that off too, if there is such a setting.

Is the computer set to spin down the hard disks whenever possible?  You need to go through all of the power management settings and try them all.

How about the screensaver?  Is it set to lock the screen?  What time delay setting does it have?

My laptop is set to **never** put to sleep. It puts the display to sleep after being inactive for 30 minutes, and it is set to **not** spin down hard disks when possible. 

So far the only idea I have is that this is caused by the display turning off - but what possible effect could this have on the speed of my computer?

---

### Post by SnickerSnack on 2010-04-17
> **Xorlathor said:**
> My laptop is set to **never** put to sleep. It puts the display to sleep after being inactive for 30 minutes, and it is set to **not** spin down hard disks when possible. 

So far the only idea I have is that this is caused by the display turning off - but what possible effect could this have on the speed of my computer?

And the screensaver?  Is it set to lock the screen?

---

### Post by Xorlathor on 2010-04-18
> **SnickerSnack said:**
> And the screensaver?  Is it set to lock the screen?

No screensaver, no locked screen. Both are disabled.

---

### Post by Xorlathor on 2010-04-20
Anybody have a solution here? This is a serious problem for me!

---

### Post by jignesh272 on 2010-04-23
Hey i also have same problem where when it goes in to sleep and after when i come back to it it just takes long to come back to its normal speed. and just side this why dont you just use vitual box in ubuntu where you can run your windows...it works i have tried it but its you coice...:lolflag:

---

### Post by SnickerSnack on 2010-04-24
> **Xorlathor said:**
> Anybody have a solution here? This is a serious problem for me!

> **SnickerSnack said:**
> You are running 10.04 right?  Which beta release, or alpha?

Maybe you won't have this problem with the official release in a week.

---

### Post by Xorlathor on 2010-04-24
> **SnickerSnack said:**
> Maybe you won't have this problem with the official release in a week.

Yea, I'm going to clean install the final version of 10.4 when it comes out in a couple days, I'll let you know if it's fixed.

---

### Post by Xorlathor on 2010-05-05
Reinstalled Lucid when the LTS came out, never had a problem since. Marked solved.

---

