---
title: "Terminal locked to foreground in Unity2d"
date: 2011-11-20
forum: Desktop Environments
---

### Post by Michael_K_Vegfruit on 2011-11-20
I'm using Unity2d in Ubuntu 11.10, on an MSI Wind U100 with Intel graphics.  When I launch terminal, it locks in the foreground.  <strike>Additionally, I cannot access menu items from the global menu.</strike> {edit: I can access menu items, but they remain hidden behind the window; see my post, #3, below]  I can switch to other apps using alt+tab, but Terminal remains on top.  This means that I can't, for example, switch to Firefox to check commands to enter (my default behaviour when using terminal, I'm fairly newb-y and generally need to work from a step-by-step guide) or <strike>adjust the transparency of the terminal window so I can read through it.</strike> [edit: fixed this, see below]

Any advice? 

This seems to affect other users in Unity2d: here's a [help request on another site]("http://superuser.com/questions/351496/why-does-the-terminal-in-unity-2d-ubuntu-11-10-always-stay-in-the-foreground").  I can't see it on Launchpad or here.

---

### Post by Paddy Landau on 2011-11-20
I suspect you have a rule in Compiz to make it on top.

When you open a terminal, right-click the title bar. Is there a tick next to "Always On Top"? If so, click it to clear it.

Let me know what happens; we can then look at Compiz if necessary.

---

### Post by Michael_K_Vegfruit on 2011-11-20
My understanding was that Unity2d doesn't use Compiz. Your advice has helped me a little though: I realise now that the menu dropdowns aren't failing to show up, but the window is on top of them.  I can drag (although still not reorder) the window, so was able to set transparency: now the drop down from the title bar right click shows up behind the window itself.  "Always on top" isn't selected.

---

### Post by Paddy Landau on 2011-11-20
> **Michael_K_Vegfruit said:**
> My understanding was that Unity2d doesn't use Compiz.
Oops, sorry!

I think I'd best leave any further replies to people who know 2D better.

---

### Post by Michael_K_Vegfruit on 2011-11-20
No problem, and thanks, you lead me to try a couple of things I hadn't before.

---

### Post by Antimethod on 2011-11-22
I have the same problem under Unity2D, though I have to add that the problem appears only when on dual-monitor for me.

---

### Post by lifeboy on 2012-06-14
Well, I'm running 12.04 in Unity2D with dual monitor setup and nothing I can find fixes this bug.

Has this been resolved since the original report?

---

