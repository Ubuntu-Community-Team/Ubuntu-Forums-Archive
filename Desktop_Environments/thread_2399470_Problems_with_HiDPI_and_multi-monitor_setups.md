---
title: "Problems with HiDPI and multi-monitor setups"
date: 2018-08-25
forum: Desktop Environments
---

### Post by mephisto26 on 2018-08-25
Good evening!


Due to a new laptop (HP EliteBook 1040 G4) I recently made a clean install of Ubuntu 18.04, after having rather happily used Ubuntu 16.04 before on an older machine.

I tried Xubuntu 18.04 first, but found adjusting all parameters to make the appearance of the desktop suitable to the 4K display tiresome to say the least. In the end I did not find a solution I was happy with (many symbols and some text still too small or too large etc.) and went back to Ubuntu then.

Ubuntu 18.04 scaled nicely on the laptop itself straight out of the box. The trouble just came when I tried to use a three monitor setup (laptop screen in 4K and two FHD displays attached using DisplayPort and HDMI, respectively). First, scaling (200%) could not be changed per monitor and was clearly wrong for the two FHD monitors (way too large). After some searching I found the info about logging in using Wayland and then enabling fractional scaling like described in the following link: [https://www.omgubuntu.co.uk/2017/09/enable-fractional-scaling-gnome-linux](https://www.omgubuntu.co.uk/2017/09/enable-fractional-scaling-gnome-linux). This solved the scaling problem for me, as I was now able to scale the FHD monitors to 100% and the built-in display to 200%.

However, this setup did not work with a colleague's triple monitor set-up (same laptop plus two 2,560 x 1,440 monitors attached via DisplayPort). With all monitors attached, my machine froze with the fans roaring. Only a set-up with one additional monitor worked.

In addition to this problem, and going back to my case (two FHD monitors), Ubuntu 18.04 restricts the application display, the app switcher (Alt + Tab) overview and the top bar to the primary display only. This is a major productivity hindrance. I tried to set one of the external monitors as the primary display, but this reproducibly broke my Ethernet connection (via docking station), which amazes me and does not sound like a hardware issue but rather an OS issue. To make matters worse, after going into stand-by (lock screen) one of the three displays can remain black from time to time after a re-log-in. This can usually be fixed by locking the screen again and another re-log-in. Alas, this is a productivity nightmare as well.

What I did not try yet is the Multiple Monitors Add-On as I read some comments stating that it does not play nicely with Ubuntu 18.04 (yet): [https://extensions.gnome.org/extension/921/multi-monitors-add-on/](https://extensions.gnome.org/extension/921/multi-monitors-add-on/).

To sum it up, did some of you have similar problems with HiDPI scaling and multi-monitor set-ups (with differing resolutions) and how did you solve them? Is there a better Ubuntu-based DE for this use case?

Your help would be greatly appreciated as I am at a loss here. One would think that this should not be an issue in mid-to-late 2018 anymore.


Thank you very much and have a nice evening (or morning or afternoon, whatever it is)!

---

