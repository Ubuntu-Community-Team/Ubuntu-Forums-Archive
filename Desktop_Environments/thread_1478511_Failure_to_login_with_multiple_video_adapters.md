---
title: "Failure to login with multiple video adapters"
date: 2010-05-09
forum: Desktop Environments
---

### Post by tsilb on 2010-05-09
Forgive my ignorance, for I am a complete linux noob.

I have a computer with three video cards and six monitors.  Works great on Windows. Trying to get it to run Ubuntu as well.

It loads fine when I have it configured to run on one adapter; detects both screens, runs ok. But I want to turn the other 4 monitors on and run the whole thing as one extended desktop (one session, etc).

So I downloaded and installed the newest ATI driver for Linux, which seems to work, kinda. I ran this to set up the screens:

aticonfig --adapter=all --initial -f

Now when I boot, Ubuntu seems to turn on all the screens (3 viewports, each with two cloned displays from what I can tell).  When I enter my login info OR move the mouse off the main screen, the screens freeze and the kbd/ms become unresponsive.

aticonfig generated attached xorg.conf. Renamed to .txt so I could upload it.

Have tried the following:
- aticonfig -initial -f    - works, but only detects the primary adapter and 2 screens
- aticccle                   - Tells me I have to reboot after enabling the other cards. Then goes into above described freezing state.
- aticonfig --adapter=all --initial -f        - see above
- Manually editing xorg.conf file with my limited knowledge - Was able to get two adapters running, but only the second adapter initialized while the primary stopped at the Ubuntu boot screen.  Was unable to see the login prompt.  Froze after I logged in blindly (was able to hear the login sound).
- Using generic "radeon" driver instead of ATI Proprietary driver with the above init attempts
- Toggling xinerama
- Various combinations of the above

Hardware:
- Intel Core 2 Quad q6600
- 8GB DDR2
- (3x) ATI Radeon HD 4680
- 5 monitors (21W, 21W, 22W Portrait, 22W Portrait, 19")and an HDTV (26"W, HDMI) in a horizontal arrangement

I know next to nothing about Linux/Ubuntu aside from basic filesystem navigation, editing text files, and accessing my local and networked Windows stores and shares. Basically this is the most advanced thing I've had to do.  I installed today.

Please advise how to make this configuration work.

---

