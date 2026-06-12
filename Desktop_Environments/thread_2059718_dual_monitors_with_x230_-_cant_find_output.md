---
title: "dual monitors with x230 - cant find output"
date: 2012-09-18
forum: Desktop Environments
---

### Post by phoe2693 on 2012-09-18
Having trouble getting my lenovo x230 working from it's dock connected to dual samsung b2240 monitors.  It uses the intel integrated graphics, i915.

The problem appears to be that it cant find the named output ports.  It only shows the default - the VGA1, HDMI2 outputs are referenced in the logs but do not show up as available for anything to use when in X. Perhaps an issue with udev?

Ive read and tried just about everything I can find - updated kernel, added newest intel drivers, looked at xrandr, and no luck at all.  Running the latest 3.6 kernel right now, but have tried the stock and the 3.4 at one point.

On install the laptop works correctly without docking, but when docked requires the nomodeset option to get X to startup.  In the dock it will display correctly on the first monitor, but when viewing the Display settings it only shows one, and labels it as laptop.  Running xrandr shows the display as "default".  

Ive also tried:
adapting this - -http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/

running xdiagnose

read through and verified this : [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

The most similar post Ive found has been : [http://www.linuxquestions.org/questions/linux-desktop-74/ubuntu-10-04-xandr-cant-change-video-resolution-808058/](http://www.linuxquestions.org/questions/linux-desktop-74/ubuntu-10-04-xandr-cant-change-video-resolution-808058/)

But I have yet to make any headway on this at all.  Monitors, cables, and ports are all verified working, and indeed show up in windows7.  Any suggestions on where to start?

---

