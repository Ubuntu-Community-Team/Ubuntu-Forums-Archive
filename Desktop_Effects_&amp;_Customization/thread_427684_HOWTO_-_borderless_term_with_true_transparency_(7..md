---
title: "HOWTO - borderless term with true transparency (7.04, beryl, nvidia, xfce4-terminal)"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by rolf-c on 2007-04-29
There may be other ways to do this, and your mileage may vary - but this works for me.

Environment:
Ubuntu 7.04 (Feisty Fawn)
Beryl 0.2.0
nVidia legacy driver 9631
xfce4-terminal

Steps:
1.)  Install Feisty Fawn.

2.)  Install the appropriate nVidia driver.  I have an old GeForce 4200 Ti, so the driver for me is 96.31.  You can find all kinds of nVidia legacy driver info at your favorite search engine, here in these forums, or the nVidia site at [http://www.nvidia.com/object/unix](http://www.nvidia.com/object/unix) .  This is one you have to build yourself if your nVidia card is too old - but it's not  a hard build.  The instructions are pretty clear, but if you've never ever built anything could be a bit daunting.  Make a new thread for help on building the nVidia driver, or search these forums for help, or check your favorite search engine.

3.)  Install Beryl.  Use the Synaptic Package Manager at System -> Administration -> Synaptic Package Manager to do this.  The whys and wherefores of installing Beryl are beyond this howto.  Try these very forums for more info, along with your search engine of choice and the Beryl project home page at [http://www.beryl-project.org/](http://www.beryl-project.org/).

4.)  Install xfce4-terminal.  After all these steps, this is the easy part.

5.)  Launch xfce4-terminal from Applications -> Accessories -> Terminal.  It's the bottom of the two terminal entries.

6.)  Use the default menu to locate the preferences, and ensure under Appearance that the background is set to transparent, and all three of the options under Opening New Windows are unchecked.

7)  Exit that term and launch again to see your borderless, transparent terminal.  See the attached screen shot for an example.

---

### Post by FuturePilot on 2007-04-29
Gnome terminal can do the same thing if you're using Beryl or Compiz. But it still has a border.

---

