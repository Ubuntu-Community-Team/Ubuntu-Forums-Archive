---
title: "kde keyboard problem"
date: 2007-05-29
forum: Desktop Environments
---

### Post by jcaloyannis on 2007-05-29
I recently installed kubuntu on my PC. Everything worked fine. Then one day for no apparent reason the keyboard stopped working. Obviously because i installed some package or other which i can not remeber. The keyboard works fine in gnome so presumable it is not a hardware problem. I completely removed all KDE applications and reinstalled kubuntu from scratch. The problem persists. KDE seems to loose the keyboard some time during initialization. I've tried turning on/off the numlock key. For a while this works. Then when the kde display setting desktop environment the keyboard freezes and never recorvers. The mouse works fine. I've tried changing the settings but nothing works. As soon as i switch to gnome the keyboard recovers. From the symptoms i do not think that it is an xorg issue since both KDE and GNOME use the same settings. Any body with some similar problem has any ideas. Thanking you in advance for any help.

---

### Post by trevorparsons on 2007-08-28
It sounds as if you may have accidentally switched on an accessibility feature called 'slow keys' by pressing on the shift key for a few seconds. This is a showstopper that has been reported in numerous bug reports and has caused many, many users who've never heard of 'slow keys' to believe that their installation is completely broken.

eg [https://bugs.launchpad.net/ubuntu/+bug/41427]("https://bugs.launchpad.net/ubuntu/+bug/41427")

Fortunately you can turn it off with just the mouse by going to the K menu -> Control Centre -> Regional & Accessibility -> Accessibility -> Activation Gestures, and untick the first box ('Use gestures for activating slow keys and sticky keys'). Also go to the Keyboard Filters tab and untick the 'Use slow keys' box if it is ticked. Press apply and you should be OK.

---

