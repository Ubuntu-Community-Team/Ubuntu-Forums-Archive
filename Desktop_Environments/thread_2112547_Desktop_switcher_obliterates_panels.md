---
title: "Desktop switcher obliterates panels"
date: 2013-02-05
forum: Desktop Environments
---

### Post by frankvw on 2013-02-05
Hi, everyone,

I'm in the process of finalizing an install of Precice Pangolin (12.04.1 LTS) on my laptop. I'm running the Gnome Classic desktop manager.

My problem is that the desktop switcher (bottom right hand corner) always reverts back to a 2x2 layout after a reboot. When I right-click and change it to one row of 8 workspaces (as I was used to in my previous Karmic distro on that same machine) my top and bottom panels disappear, and the Ctrl-Alt-Arrow keys let me select 4 empty desktops from a 2x2 grid. And that's it - no way out except to go into a text mode console and reboot.

What gives? This used to work fine in Jaunty and Karmic. All I want is one row of 8 virtual desktops (a.k.a. workspaces) in the switcher, and have my panels in all of them, like I used to. Not too much to ask, is it? ;)

Suggestions, anyone? Tnx!!

// FvW

---

### Post by stinkeye on 2013-02-05
If your logging in to the **Gnome Classic** session then compiz is
your window manager and controls your workspaces.
Set the workspace switcher to use 1 row and 1 workspace and set your
virtual desktops in ccsm as in pic, and the switcher will adapt to the ccsm setting.
You will see the switcher change as you adjust the setting in ccsm.

**Reason:**When in compiz you really only have one desktop where you can set numerous virtual desktops.

---

### Post by frankvw on 2013-02-10
> **stinkeye said:**
> **Reason:**When in compiz you really only have one desktop where you can set numerous virtual desktops.
I hear what you say... but in that case why do I get a 2x2 workspace switcher installed by default which works, but which stops working when I change the layout from 2x2 to 1x8?

// FvW

---

### Post by stinkeye on 2013-02-10
> **frankvw said:**
> I hear what you say... but in that case why do I get a 2x2 workspace switcher installed by default which works, but which stops working when I change the layout from 2x2 to 1x8?

// FvW
If I login to the gnome classic session as guest the
setting in the workspace switcher is 1x1
but ccsm shows 2x2 and the workspace switcher draws a 2x2 grid.
This would be the default settings after a fresh install.

If I login to the gnome classic(no effects) session as guest, 
where compiz is not running the setting in the workspace switcher is 4x1.

So basically if your running compiz leave the workspace switcher as is (1x1),
and use ccsm to adjust your virtual desktops.
If your running Metacity use the workspace switcher preferences to adjust desktops.

---

### Post by frankvw on 2013-02-10
> **stinkeye said:**
> So basically if your running compiz leave the workspace switcher as is (1x1),It isn't 1x1. It's 2x2 and keeps reverting back to that.

> **stinkeye said:**
> and use ccsm to adjust your virtual desktops.I just stumbled upon the solution. I tried a "gnome-panel --replace" command, and suddenly everything now behaves again as it should (and did in previous distro's). I can now set my workspace switcher layout to 1x8 and when I switch workspaces they still have panels.

// FvW

---

