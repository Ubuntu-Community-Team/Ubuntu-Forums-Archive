---
title: "thinkpad (t500) issues with Unity"
date: 2012-01-26
forum: Desktop Environments
---

### Post by ggoforth on 2012-01-26
Hello All,

Did an upgrade recently from 10.04 to 11.10 on my ThinkPad (T500).  I'm having some issues getting used to unity, that I think if solved I would be pretty happy with the os.  

My issues are mainly graphical in nature, and I think somewhat related to dual monitors.  First, the toolbar menus at the top of each monitor will disappear in some cases where I move the position of the monitor in the displays settings.  IE if I move the secondary up, the bar on my main (laptop) monitor goes away.  

The second is that I would like to launcher to always be visible, so I downloaded compiz config settings manager, set the auto hide feature to "never" and the launcher still hides every time.  It seems to still be exhibiting the "dodge windows" settings, even though after a reboot the "never" setting is still enabled.

The third issue has to do with the menus on the top toolbars.  When I click an icon like my user name, the clock, the mail icon, etc...the menu appears and immediately disappears.  If I hold the click, the menu stays and I can find what I'm looking for, but if my cursor goes off the menu, it's gone...all previous flavors of ubuntu I've used keep these menu's open until you click elsewhere.  

I've tried unity and unity 2d all with pretty much the same results. 

Thanks so much for any ideas!

Greg

---

### Post by ggoforth on 2012-01-26
To add to this, none of the compiz settings that I change in compiz config settings manager seem to be respected.  I want to user super+tab for window switching, so I set that up in compiz, but nothing happens when I do super+tab.  I set ring switcher to that key combo, and nothing.

---

### Post by Krytarik on 2012-01-26
> **ggoforth said:**
> I've tried unity and unity 2d all with pretty much the same results.
> **ggoforth said:**
> To add to this, none of the compiz settings that I change in compiz config settings manager seem to be respected.
That's because you are always being logged in to Unity 2D, as a matter of fallback. According to the specs of your laptop I've found via a web search, at least one of its graphics devices should support the regular Unity (the ATI one):
[LIST]
[*]Intel Integrated Graphics 4500MHD - integrated graphics chipset
[*]ATI Mobility Radeon HD 3650 w/ 256 MB - discrete graphics chipset
[/LIST]
You can check the results of the Unity support test by running:
```
/usr/lib/nux/unity_support_test -p
```Actually, the open source driver for ATI/AMD graphics devices should be sufficient to support Unity, but as the proprietary driver supports your ATI graphics too, you could also try those, therefore check "Additional Drivers".

But I'm afraid this has more to do with your hybrid graphics setup, and I'm not an expert reg. that at all; the first thing I'd try, though, is to disable the Intel graphics via the BIOS of your laptop, in case it's being tried to be used for running Unity.

Hope that helps.

---

