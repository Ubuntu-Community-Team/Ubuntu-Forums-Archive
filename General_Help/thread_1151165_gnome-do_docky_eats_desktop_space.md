---
title: "gnome-do docky eats desktop space"
date: 2009-05-06
forum: General Help
---

### Post by Dougie187 on 2009-05-06
This is sort of an odd... situation.. I guess I wouldn't really call it a problem. 

Anyways, when I use docky it seems to eat up some desktop real estate. I filed a bug report with gnome-do but I thought I would post it just in case someone who doesn't use their bug system had an idea or wanted help with the same issue.

[https://bugs.launchpad.net/do/+bug/372937](https://bugs.launchpad.net/do/+bug/372937)

---

### Post by cariboo on 2009-05-07
It would help if you posted a screenshot. docky is resizable. Grab the seperator to the left of the clock and resiz to your liking. See my screenshot.

---

### Post by pbpersson on 2009-05-07
I like mine a little larger but I have it set to hidden so it only appears when I want it

---

### Post by Dougie187 on 2009-05-07
Setting the dock to auto-hide fixes the issue.

I don't really know if a screenshot would help much, but here it goes.
Basically, I can't place any icons below the pdf file named "SWPro300im.pdf"

Sometimes, if something creates an icon, it can be placed in the unusable region, but I can't move anything into the unusable region. If I resize my docky it doesn't do anything, I can make the dock huge and it still has the same issue, or I can make it small and it has the same issue. Neither one makes the unusable area grow or shrink. The few things I have found change the issue are turning on "Auto-hide" and turning on "Always show results window"

Auto-hide fixes the problem, but I don't particularly like auto-hide. And "Always show results window" worsens the problem, so I turned it off.

If you want to try it, Here are some basic instructions, and I hope they describe it well.

Make two Icons, (like the two highlighted pdfs in my screenshot).
Highlight BOTH of them. Drag the top one, and the bottom one should turn into an outline. If you drag the top one around your desktop, you should see a faded icon for the top icon, and a checkered outline for the bottom one. Now, if you drag these two down towards the bottom of your desktop, the outline should disappear after you get to a certain point. If you release the top icon at this point, you won't see the two icons placed on your desktop where you want, and they will return to to original locations.

---

### Post by DBO on 2009-05-08
this issue is fixed in bzr

---

### Post by Dougie187 on 2009-05-08
> **DBO said:**
> this issue is fixed in bzr

Awesome, Thanks!

---

