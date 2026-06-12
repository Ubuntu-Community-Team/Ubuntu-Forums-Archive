---
title: "Crazy Colors and Freeze/Crash"
date: 2008-06-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by phylae on 2008-06-13
Hi,

I have a Dell XPS M1330 with Ubuntu 8.04 on it. Recently it started randomly freezing/crashing and displaying crazy colors on the screen. It looks like this:

[IMG]http://members.shaw.ca/phylae/vlcsnap-4072618.png[/IMG]

Sometimes the colors flicker and change; sometimes they don't. Usually it will stay like that until I do a hard reset (I haven't left it much more than a couple minutes). Occasionally it will restart on its own.

Here are the specs for the system:

RAM: 4GB, DDR2, 667MHz 2dimm
Video Card: 128 MB NVIDIA GeForce 8400M GS
CPU: Intel Core 2 Duo T7500 (2.2Ghz/800MHz FSB, 4M L2 Cache)

I have the proprietary NVIDIA driver installed.

I have Googled for hours, and I can't find similar problems (with the weird colors).
What should I do to start debugging this problem?

---

### Post by phylae on 2008-06-14
My problem seems to be a duplicate of this one:
[http://ubuntuforums.org/showthread.php?t=822815](http://ubuntuforums.org/showthread.php?t=822815)

---

### Post by rated727 on 2008-06-23
The following is for your consideration:

I have a VERY OLD Dell desktop (BIOS copyright 2000)
I have had some odd behavior with the embedded Intel display (built into the system board).
On start, just before the Heron background, I got a lot of screen trash for about 1/2 second, but mine was more horizontal streaked than your photo.
Once booted, clicking the cursor would leave behind an image of the previous screen that was about 1/2 to 1/3 of the size of an icon.  I also had problems with the title bar on any opened application, no title, and no buttons in the upper right to max, min, or close.
I disabled the on-board display and installed an old Matrox video card.
***  No more problem.  ***
My guess is that the RAM of the on-board video may have been unstable and was singularly causing the problem, or (more likely) that it caused the Ubuntu installation to misidentify the display.
Oddly, this is a dual boot system with Windows 98 Second Edition and no similar problem showed under Win98 (which doesn't work the display as vigorously as Linux.  
Good Luck

---

