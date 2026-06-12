---
title: "windows maximize spontaneously"
date: 2012-03-09
forum: Desktop Environments
---

### Post by shochatd on 2012-03-09
I have become fairly comfortable with Unity since it was introduced. However, there is one behavior that I really do not like. Sometimes when I move or resize a window, it spontaneously maximizes, even though I have not asked it to. I find this extremely irritating, but I cannot figure out how to fix it. I have a large screen and I NEVER want any window to be maximized.
Thanks.

---

### Post by rg4w on 2012-03-09
I had the same reaction.  This can be adjusted with Compiz Config Settings Manager, in the Grid section.

---

### Post by shochatd on 2012-03-09
How do I bring up the Compiz Config Settings Manager? I have used it before (to make the launcher smaller), but it was in a non-obvious place, and now I can't find it at all. Also, is it now safe to use it without a risk of rendering your desktop inoperable?

---

### Post by rg4w on 2012-03-10
> **shochatd said:**
> How do I bring up the Compiz Config Settings Manager? I have used it before (to make the launcher smaller), but it was in a non-obvious place, and now I can't find it at all.
After you've installed it from the USC, enter Dash and type CCSM - you'll find it straightaway.

> Also, is it now safe to use it without a risk of rendering your desktop inoperable?Short answer:
If you limit yourself to adjusting only the items in the Unity Plugin in CCSM, you'll probably have a safe and useful time with it.

Long answer:
CCSM and Unity don't always get along, but a good many folks who love the Rotating Cube, Wobbly Windows, and other fun stuff that make up some of the more entertaining aspects of our Linux heritage have posted instructions for using those - here's one for the Cube:
[http://ubuntuforums.org/showthread.php?t=1892851](http://ubuntuforums.org/showthread.php?t=1892851)

In my experience, since the advent of Unity the Cube can be made to work but not nearly as gracefully as before.  I'm not talking about event bindings like dragging windows from screen to screen conflicting with Unity's default in CCSM's Grid settings for window layout - those can be resolved by just taking a moment to think through which behavior you want and set those options accordingly.  Instead, I'm talking about redraw issues, flickers and other anomalies that were never an issues prior to Unity.

These and other problems have raised a question which has been raised on the unity-dev list and elsewhere:  is the source of these bugs CCSM or Unity?

CCSM seems an easy target for blame, since it has few resources to maintain it.

But in all fairness, CCSM worked fine by itself for quite a long time, with some of the biggest problems becoming evident only after Unity was introduced.

This doesn't necessarily mean that Unity is inherently buggy or even the source of any conflicts with CCSM.  Only a thorough code analysis can identify the true core issues, and to the best of my knowledge no one's yet had the time to do that thoroughly.

My own hunch (and this is only a hunch) is that Unity simply may not take into account any CCSM settings other than the ones it uses by default as shipped with the system.  So as long as you don't change anything in CCSM Unity generally runs well, but once you introduce change, even change to long-standing settings, Unity does not appear to do a thorough job of accounting for such possibilities.

To be fair to the Unity team and to Canonical, I think it would be a bit of a stretch to ask that Mr. Shuttleworth fund the level of error-checking and providing graceful degradation that would be needed to allow Unity to be fully compatible with CCSM.    CCSM is deep, and full compatibility with everything it offers would take a lot of engineering resources that I'm sure Canonical feels would be better applied to more commonly-used features and new innovations; I trust most would agree.

But on balance, the Linux community has become fond of things like the Roating Cube and other popular CCSM effects, and indeed many of those have come to define the freedom and flexibility that distinguishes Linux from other OSes.

In the short term, all this means that we need to tread carefully in CCSM, and thankfully the Ubuntu devs added a warning dialog for 12.04 which notes the risks and have left it available in the USC.

For the long term, I think an ideal would be to see CCSM become for 12.10 the sort of Power User Settings Panel it always has been in pre-Unity versions, but without conflicting with Unity.

So I wonder:  if those of us in the community who love CCSM could put together something like a Kickstarter fund for enhancing CCSM to be more compatible with Unity, which may likely require bug fixes/enhancements in Unity itself, could we convince Canonical to accept such enhancements?

If so I'd love to see this happen.  It seems the best of all solutions:  those who love the flexibility of CCSM would still get to enjoy it going forward, and the cost to Canonical would be close to zero.

---

### Post by shochatd on 2012-03-10
Thank you for the extended and detailed reply. I had actually discovered that I could bring it up by searching for "compiz" in the Dash. I had been looking under System Settings... which is where I think these things belong. But not by that name! I assume (and maybe you can tell me whether this is the case), that compiz has some sort of well-defined API which CSSM uses to configure it. So what I think Ubuntu needs to have is a carefully-chosen subset of CSSM's functionality provided in an intuitively-named item under System Settings, e.g. "Unity Settings". This should provide at least:
1. Adjusting the size of the launcher.
2. Adjusting criteria for appearance and disappearance of the launcher.
3. Enabling/disabling auto-maximizing of windows.
This would be an alternate front-end configuration tool for compiz (or for Unity 2-D on systems that use that). CSSM should still be there as you say, with warnings, for power users who want rotating cubes and all that.
-- David

---

### Post by rg4w on 2012-03-10
> **shochatd said:**
> ...So what I think Ubuntu needs to have is a carefully-chosen subset of CSSM's functionality provided in an intuitively-named item under System Settings, e.g. "Unity Settings". This should provide at least:
1. Adjusting the size of the launcher.
2. Adjusting criteria for appearance and disappearance of the launcher.
3. Enabling/disabling auto-maximizing of windows.
I would support those with the addition of:
4. Ability to tailor the background color behavior.

This is in the CCSM Unity Plugin, but absent from the 12.04 Settings panel, and is a small but important detail:

The current design of the Launcher tries to determine the dominant color of the icon and use that to fill in the surrounding rectangle.  The problem with this is that with icons like the ones for Nautilus, Software Center, and others, adding the color obscures the outline shape of the icon, making it difficult to distinguish.

Using the Unity Plugin I set mine to use the background color only for open apps, so when I want to open one the shape is more easily recognized, and those that are already open are readily distinguished from those that aren't.

Perhaps it may be even better to just adopt either my settings as the default or to ditch the background color altogether.

PS: A good midpoint between the limits of the Settings panel and the conflict between CCSM and Unity is MyUnity, a nifty app coming to the USC which provides most of these settings and more in a reasonably safe and very attractive UI:
[http://www.omgubuntu.co.uk/2011/12/unity-tweak-tool-myunity-gets-new-look-coming-to-ubuntu-software-centre/](http://www.omgubuntu.co.uk/2011/12/unity-tweak-tool-myunity-gets-new-look-coming-to-ubuntu-software-centre/)

---

