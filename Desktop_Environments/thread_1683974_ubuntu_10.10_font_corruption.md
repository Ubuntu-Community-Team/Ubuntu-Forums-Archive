---
title: "ubuntu 10.10 font corruption"
date: 2011-02-08
forum: Desktop Environments
---

### Post by swdinesh on 2011-02-08
I installed Ubuntu 10.10 64 bit on my new hardware.
I'm using an LCD monitor in HDMI input at resolution 1920x1080 (60Hz).
I've corruption of the font after a while that the gdm is running (sometimes earlier sometimes later). The corruption is that some characters are shown as a white square and not the character itself. 
I tried to change font and sub-pixel settings of the font, but it didn't fix the issue. Changing the sub-pixel order from RGB to VRGB fixes the current problem but after a while I have the same problem on other characters.
My font dpi is set to 96.

Can anyone drive me in a direction that helps me to fix this problem?

thank you
Alex

---

### Post by w3rt on 2011-02-08
pretty sure I saw this issue on IRC, i think changing the font fixed the problem for the person experiencing it

---

### Post by swdinesh on 2011-02-08
thank you w3rt , but this was the first thing I did, but is a problme of rendering not a problem of the font. I tried differrent kind of font , but the problem is always here :(

---

### Post by rattskjelke on 2011-02-08
I had the font problem earlier. See this post: [http://ubuntuforums.org/showthread.php?t=1616033](http://ubuntuforums.org/showthread.php?t=1616033)
My problem seems to have cured itself in the past couple of months. It hasn't happened lately. There may have been an update that fixed it. I never figured out what was causing it.

---

### Post by rattskjelke on 2011-02-16
> **rattskjelke said:**
> 
My problem seems to have cured itself in the past couple of months. It hasn't happened lately.
I spoke too soon. The problem returned today.

---

### Post by DMJ on 2011-02-23
I had the same issue, but it went away after switching to the proprietary ATI driver. However, the proprietary driver caused excessive memory use that gradually increased the longer the system was up. It also caused Cairo Dock to flicker in OpenGL mode. 

The memory problem made it so I couldn't use VM's. running the top command showed Xorg to be using an unusual amount of memory. That's what tipped me off. A found a number of posts by other people using ATI adapters with the same problem. 

I've switched back to the open driver for now. I'm going to try installing the new driver from ATI instead of using the one from the repos, when I have the time.

---

### Post by DMJ on 2011-02-23
Note that I haven't had these problem's on my 7 year old Toshiba laptop which has an NVIDIA adapter. Even though it has PC2100 memory pulled from my Dell (it's supposed to take PC2700) I could run it with an XP VM, firefox and Chrome both open with a dozen tabs each, and several other programs. I'm running 10.10 32-bit on the laptop, and 10.10 64-bit on my PC.

---

### Post by swdinesh on 2011-02-25
I have my pc and my laptop installed with 10.10 and I experience the same problem. Both of them are running ATI driver.

I have a temporary solution changing the setting Font -> Details -> subpixel order, but the problem re-appears after a while.

I'm trying to use a setting different like best contrast to see if the problem re-appears. I'll keep posted

---

### Post by DMJ on 2011-04-02
I've switched over to Linuxmint 10, because it has a lot of the benefits of Ubuntu but a friendlier interface. But I'm still having the same issue. With the ATI driver I get a memleak, but without it I get the black squares. Turns out it has something to do with OpenGL. if I run Cairo Dock w/o openGL there's no font corruption. The problem had gone away on Ubuntu, but it didn't occur to me that it was because I wasn't using gl with CD. 

So now I know where the problem's coming from, is there a solution?

---

### Post by rattskjelke on 2011-08-03
Several months ago I switched to Linux Mint 10 and then 11 to see if the same thing happened.
I still had the font corruption problem.
Somebody posted in the Linux Mint forums about another video problem I was having that I think might be related.
They posted this link to another site [http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/](http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/)
I tried the fix (step 9. in the article) and it appears to have fixed the problem.

---

### Post by DMJ on 2011-08-05
The issue is due to graphics drivers. I upgraded to Natty and had all sorts of artifacts with the FOSS driver. These went away with the ATI driver, but then I had a massive memory leak. I've since replaced the onboard graphics with a dedicated NVIDIA card. My system works great now. The only issue is that I still get a memory leak when doing TTY switches. Otherwise, no problems. Hopefully the anticipated switch to Wayland will resolve most of the graphics issues, but that's long-term. Short-term it will probably cause more issues than it fixes. The key is if it makes writing graphics drivers easier. The only graphics I've used with flawless results are Intel.

---

### Post by rattskjelke on 2011-08-08
I was wrong. That didn't fix it.

---

