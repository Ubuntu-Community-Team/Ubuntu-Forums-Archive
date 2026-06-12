---
title: "Spontaneous changes to text-scaling-factor"
date: 2014-08-09
forum: Desktop Environments
---

### Post by andy36 on 2014-08-09
I am running ubuntu-desktop (unity) on a very recent install of 14.04 server, but I had the exact same problem with a desktop installation on the same machine last week. I have three monitors plugged in, but one is a TV that I usually have turned off The current setup is with a nvidia geforce 750 Ti card, but I had the same problem on the same machine jusing just the Intel Core i5 onboard graphics (and only two monitors). The monitors are connected by DVI, Display-port-to-HDMI, and the TV by straight-up HDMI. The non-TVs are rotated 90-degrees (portrait).

In Settings --> Display, the "Scale for menu and title bars" is set to 1 for all monitors.  The output of org.gnome.desktop.interface text-scaling-factor is 0.5625. Back when I was having the same problem with the Core i5 graphics, I installed the unity-tweak-tool as a workaround to this problem and found that this setting commonly reverted to that same number: 0.5625. I can drag the slider around for this menu/title bar scaling and change things bigger and smaller, but when I leave it on 1, the text-scaling-factor is 0.5625. If I adjust the setting to make the text be closer to 1 (i.e. large and legible), the title bars are huge and obnoxious. Related: The "Scale all window contents to match" setting in display gives inconsistent results--sometimes both monitors seem to do what I ask, sometimes the text size is different on them even though they should be synchronized.

Note that this same bug has been reported here: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1310316](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1310316) ... but I  don't know what the relationship is between that forum and the one I am posting in right now.

Anyway, has anyone around here experienced this annoying behavior? Does anyone know how to fix it?

---

