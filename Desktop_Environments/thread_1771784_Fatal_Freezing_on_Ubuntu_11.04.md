---
title: "Fatal Freezing on Ubuntu 11.04"
date: 2011-05-30
forum: Desktop Environments
---

### Post by redbikemaster on 2011-05-30
Here's yet another problem I've been having with 11.04. I'll be working on anything, then the screens (dual-screen setup) go black, any sound that was playing goes into a loop, then I get scrolling white text on a black screen. Sometimes the mouse is left frozen over the text. Then the Caps Lock, Num Lock, and Scroll Lock lights flash. I have to restart to get out of it. This morning, over two hours I had to restart five times.

I have to have a reliable computer! I can't be having problem after problem!

---

### Post by redbikemaster on 2011-05-30
Some more info. Last night my hard drive started sounding like it was spinning up, then it would click. Over and over. Sometimes on startup I get an error message on the Ubuntu startup screen saying something like it couldn't mount / (root).
I tried doing a self-test through Disk Utility, then the drive made that same noise (see above) then the test said, 'Cancelled (with hard or soft reset)'.
Could all this be caused by a dying hard drive?

---

### Post by lifelike27 on 2011-05-31
I've been experiencing the same symptoms and I did notice the hard drive click noise recently, however I haven't heard it again. My laptop is less than a year old so I don't think the hard drive could be dying so soon.

I have a feeling it might have something to do with Chrome because I haven't had this problem since I disabled one of the plugins for Adobe Flash 10.3 beta. Since that's the only change I've made since I've been getting these random freezes, I'm assuming that MIGHT be the cause.

I'm using firefox now and so far, no freezes. Will uninstall and reinstall chrome.

---

### Post by redbikemaster on 2011-05-31
OK, I started using Firefox instead of Chrome (I have both for different uses) and it was fine for a couple of hours then the computer did the exact same thing then had trouble restarting.

Just an update.

---

### Post by dFlyer on 2011-05-31
can you use disk utility and check for bad sectors. I had a hard drive fail that was only 6 months old, so age of a computer really means nothing, when it comes to hardware. You might also want to check your memory.

---

### Post by redbikemaster on 2011-05-31
I checked it, and it returned a warning on Reallocated Sector Count. Its score was:
Normalized:100
Worst:100
Threshold:10
Value:1 sector
See above for other info.

---

### Post by redbikemaster on 2011-05-31
I just emptied half of the primary hard drive. I'll update whether or not this fixed it.

---

### Post by redbikemaster on 2011-06-02
Almost went a full day without freezing, but it happened twice in the past five minutes. Every time it freezes, it requires two restarts. The first one freezes up right before the Ubuntu startup splash.

---

### Post by petoro on 2011-06-08
My Narwal also freezes one time a day or so.

Mainly when I'm not using the computer.

The mouse movements work, but the clicks or the keyboard not.

The clock on the upper right corner also freezes.  In fact, the stopped seconds is the first thing I watch to see if the computer has hanged.

Alas, I don't restart the computer:

1.- I log out the computer to the terminal by pressing CTRL + Alt + F1

2.- In the terminal I type my login and pass

3.- Then I write 'sudo pkill X' (without the commas)

And then I enter in the windows mode finally.  The problem is that all the programs I was using have disappeared.  It is as a clean boot save that it is faster.

I tend to consider that it is a memory problem, but I am not sure.

---

### Post by redbikemaster on 2011-06-09
Well it appears the hard drive totally died so I swapped in a PlayStation 2 hard drive. Had a couple kernel panics during install, but it's working now.

---

### Post by lifelike27 on 2011-06-13
redbikemaster, I did some searching on launchpad.net and it turns out the reason I was having freezing problems is because of the wireless network I was using previously. My wireless card would crash at some point when using that network.

I haven't used that wireless network since and it hasn't crashed!

---

### Post by redbikemaster on 2011-06-15
And it is still freezing!!! ARGH!

I was told that I might have a corrupt kernel. How would I fix that?

---

