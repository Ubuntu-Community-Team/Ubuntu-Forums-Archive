---
title: "Apps launching with window title HIDDEN BELOW panel (Gnome Classic)"
date: 2013-07-17
forum: Desktop Environments
---

### Post by r_avital on 2013-07-17
Been going around in circles with everything I've found on google and here about this, but none of the resulting articles/posts seem to address this:

Fresh, clean install of 12.04 LTS, using **strictly Gnome Classic and Gnome Classic - No Effects sessions** (installed the fallback package, obviously).

In both environments, everything was normal, untill I installd Compiz settings manager (the buggy one, that's distributed with Precise, of course).

As soon as I installed CCSM, logged out/back in, and:

In Gnome Classic No effects -- well, no effects, so everything is still normal.
In Gnome Classic (WITH effects), every app opens with the windows title-bar hidden below my top Gnome panel.  Not merged, mind you, hidden.

Though it appears as though the window has no title-bar, I can grab the window (Alt+F7 in my case) and drag it down, the title-bar is there nice and pretty.  At one point, the title-bar disappeared altogether, so I checked CCSM again, and re-enabled the Windows Decorations plugin, and chucked it off to CCSM's bugginess.

If I completely purge Compiz, in the Gnome Classic (WITH effects) session, everything is normal again.

[Aside: Wasn't there supposed to be a fixed version of Compiz/CCSM released for Precise?  I know I could downgrade Compiz to a previous version available through a PPA, but on launchpad.net/ubuntu there is an entry stating that the "features" -- i.e. bugs -- in the current Precise -related version of Compiz have already been implemented in that older version.  I tried it anyway, with identical results.]

I'm willing to go to any lengths to solve this problem, install additional packages, edit configuration files, anything any of you can come up with, so all suggestions are welcome.  I only beg you on my bended knees -- "use something else" (like unity) is **not** a solution.

TIA :)

---

### Post by dino99 on 2013-07-17
not everything works with compiz : stay with the default ubuntu settings

dconf reset -f /org/compiz/

---

### Post by r_avital on 2013-07-17
I know you were trying to be helpful, and I'm grateful for that.  But this, please don't take offense, is exactly the kind of answer I was begging not to get.

I think I'll stay with Lucid where everything DOES work with Compiz, until, maybe somday, a non-buggy LTS comes along.  Windows wasn't this bad.

---

