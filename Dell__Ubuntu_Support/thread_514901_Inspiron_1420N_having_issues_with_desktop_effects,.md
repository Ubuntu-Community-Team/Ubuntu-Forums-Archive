---
title: "Inspiron 1420N having issues with desktop effects, etc"
date: 2007-08-01
forum: Dell  Ubuntu Support
---

### Post by KillerSiafu on 2007-08-01
I just got a 1420N running fiesty fawn from dell with hardware information as follows:

Processor: Intel Core2 Duo T7300 @ 2Ghz
Memory: 2 Gb
Graphics Card: Intel Mobile Integrated Graphics Controller


So I'm having a few problems.

**1) **When I enable desktop effects, (without turning on the wobble or cube checkboxes) and I try to minimize a window (can be any directory or application window), the window gets about halfway minimized and the system freezes.

**2)** When I enable desktop effects and enable workspaces on a cube effect, the system freezes, although I can still move the mouse. The keyboard and mouse buttons are non-responsive however.


So obviously I disabled desktop effects, and those problems don't persist, although I'd like to know if there is a solution.


**3) **Then, i opened up the screensaver preferences, just to see what kind of screen savers were available, and when I change to a different screen saver (instead of blank screen) it tries to preview that screen saver, but instead freezes on a black screen.


And finally, this last problem is sort of random, but perhaps the most annoying.

**4)** I'm unable to install any firefox plugins. I've tried installing fireftp, new tab button on toolbar, newtaburl, download statusbar, colortabs, and temporary inbox. All extensions I've used on other machines successfully. When I attempt to install from mozilla's site, I get a -228 download error. I went to mozilla's troubleshooting site which said to download the extension to your desktop and drag it into a firefox window, which I did. Still no luck. Firefox has been updated and is running the current version.

Sorry for the lengthy post... Anyone have any insight or any of these issues?

---

### Post by KillerSiafu on 2007-08-01
I was semi-able to resolve issue #3. I found another post addressing this issue, which can be found here:

[http://ubuntuforums.org/showthread.php?p=2881389](http://ubuntuforums.org/showthread.php?p=2881389)


As for issues 1,2 and 4... still up for grabs

---

### Post by sciurus on 2007-08-01
For 1..3 see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104673](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104673)

---

### Post by KillerSiafu on 2007-08-02
Thanks for the post scirius... That did seem to help. I no longer have any problems with screen savers and the desktop effects ive tried have worked so far. I'm still cautious of trying the cube again after the pain it caused me to undo it the last time I tried. I'll prolly just install beryl instead.

Still haven't figured out what the hell could be causing #4 however.

---

### Post by phynix on 2007-08-09
I have a 1420n with the same problems. It would freeze when I tried desktop effects. This worked for me

[http://ubuntuforums.org/showthread.php?t=506744&highlight=965+compiz](http://ubuntuforums.org/showthread.php?t=506744&highlight=965+compiz)
 make sure you read the whole first page. Cause if you don't you will boot into command

and this is just a random  one if you want  your scroll bar on the side to work

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Scrolling_feature_on_touchpad_does_not_work)

hope this helps

---

