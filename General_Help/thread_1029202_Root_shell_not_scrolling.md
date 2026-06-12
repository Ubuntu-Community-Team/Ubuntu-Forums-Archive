---
title: "Root shell not scrolling"
date: 2009-01-03
forum: General Help
---

### Post by Mizipzor on 2009-01-03
Hi. I booted my ubuntu box after being shutoff for a while. 319 updates wanted to be downloaded. I did that and then hell broke lose, nothing works.

But the most severe problem is that the screen isnt handled properly. The X server refuses to start, tries a couple (from the looks of it) resolutions and then gives up. Pressing ctrl+alt+f2 gave me this shell where I could login, install links and browse here in dire need of support.

The links window itself scrolls, thats why I can type this. But I have no idea at all on what the next step could be. Reinstalling x server? Gfx drivers?

At least I got internet access so I could pastebinit some config files.

Please, help me save my box, it became quite useless with the update.

---

### Post by RealPSL on 2009-01-04
Try reconfiguring the X server with ```
sudo dpkg-reconfigure xserver-xorg
```

---

