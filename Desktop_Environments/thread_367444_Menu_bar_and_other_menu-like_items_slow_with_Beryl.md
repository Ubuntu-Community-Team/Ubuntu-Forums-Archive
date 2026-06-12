---
title: "Menu bar and other menu-like items slow with Beryl"
date: 2007-02-22
forum: Desktop Environments
---

### Post by mawdryn on 2007-02-22
Hi,

I'm using Beryl 0.2.0 RC3 on Ubuntu 6.10, and am finding that when Beryl is set as the Window Manager, the Ubuntu Menu Bar and any application's main menu is slow to respond, ie you click on the menu and wait 2 seconds before the menu pops up. Every other element of Beryl runs at top speed, and the Beryl benchmark gives a nice steady 85 FPS 

I'm using an nVidia 7300GT and xorg is configured with the binary nvidia driver 1.0-9746, 

I've been right through the Beryl settings and cannot find anything relating to menu delay.

Any help appreciated.

---

### Post by mawdryn on 2007-02-23
After some further investigation, I've found that disabling the additional monitor fixes the problem. It appears that there is still a bit of work for the developers of Beryl regarding multiple monitor displays as my additional monitor when enabled doesn't completely work with Beryl. 

Hopefully a future update will address this problem.

---

