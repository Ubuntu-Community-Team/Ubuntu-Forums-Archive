---
title: "Mangled window manager, desktop nearly useless"
date: 2010-04-18
forum: Desktop Environments
---

### Post by drreed on 2010-04-18
Well I did it. I was bored and wanted to play with compiz-fusion. While trying different effects, other things quit working. I have now removed compiz-fusion, but the problems persist.

Here is what I need to fix (and don't know how):
1. Windows no longer have minimize, maximize close, or the "roll-up" button.
2. Windows manager and windows manager tweaks are just blank screens. If I try to run each individually from the menu, nothing happens.
3. Windows won't resize or move. 

I have to go file>quit to see windows in behind the one with focus.

---

### Post by bigsmitty64 on 2010-04-18
Not a 100% here but, If it was me I would re-install compiz now. Sounds like what ever you did needs to be fixed with compiz.

---

### Post by drreed on 2010-04-18
> **bigsmitty64 said:**
> Not a 100% here but, If it was me I would re-install compiz now. Sounds like what ever you did needs to be fixed with compiz.

Heheh . . . Thats what I was thinking . . . I'm in another distro right now, so I'm not shutdown or anything. Xubuntu is where I have all my general/misc music, videos, downloads and all that nonsense.  What would I do without 'mount'? 

If no xfce4 guru's show up I may have to try that.

I wish I could just re-install those components, but I don't know what they're called!

---

### Post by drreed on 2010-04-19
Solved

Re-installed compiz and emerald.  Most functionality returned, still had to set top margin where no windows could be to avoid hiding them.

Installed almost every available nifty panel feature.
You have to have a separator in your panel to have items on both left & right ends of the panel.

If you want your workspace switcher back in the default position after deleting your panel you add a separator and make the workspace switcher the next item you add, it will go to the right panel end. Each one you add after that progresses to the left. I still haven't been able to move an item. It's on the context menu though.

Also, I unchecked the property that makes it show all open items on all workspaces, trying to get it to only show windows minimized in the current workspace. I'd like to make more use of that extra workspace, and get used to switching back and forth using the workspace switcher. With the minimized icon on the panel, it's hard to break the habit of clicking that. (Which brings it in to the current workspace, even if you want it in the other) By not showing the icon, it'll force to switch. That I still have to figure out.

My ATI card though powerful, apparently won't support some of the slicker compiz effects (like cubes and such).  Yet another disappointment wrought by ATI. Compiz is still capable of producing many neat theme effects using the stock ATI driver that ubuntu installs. All in all, compiz is pretty neat. What I'll do if I have to uninstall it again though, who knows?

** Update **

I booted up today and the theme stuff that was working ok last night had the cpu pegged at 100% just sitting at the desktop with no windows open. I changed numerous items, compiz --replace'd, and still couldn't free it up.

I removed compiz & emerald and then systatically removed and installed windows manager components until I got xfwm4 working again. I did learn a little about what's possible and how all of these components work together to make a desktop.

Result: 20 minutes after restoring xfwm4 I have a really slick looking desktop that's FAST and COOL!

Just say no to compiz & emerald, unless you want Windows XP + McAfee + Hidden Trojans performance from your Linux.

---

