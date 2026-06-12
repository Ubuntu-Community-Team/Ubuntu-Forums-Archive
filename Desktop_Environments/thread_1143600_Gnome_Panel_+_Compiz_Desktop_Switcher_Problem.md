---
title: "Gnome Panel + Compiz Desktop Switcher Problem"
date: 2009-04-30
forum: Desktop Environments
---

### Post by shrimpy89 on 2009-04-30
Hey all,
I'm running Jaunty, and I'm enjoying it for the most part (aside from the odd lock-up once in a while...).  However, when I switch desktops with Compiz Cube enabled, the window list for ALL desktops remains on the bottom panel.  When I click the button, it spins the cube back to desktop number one and opens the window there.  No matter what desktop I have a window open on, the button for it always appears on the bottom.  This is pretty inconvenient when I want to hide a game I'm playing when I'm supposed to be taking notes in class. :P  This problem doesn't exist with effects turned off.  I wouldn't mind going without the useless fun of compiz, but...what can I say, when battery life and processor speed aren't issues, I'm a sucker for effects like that.  I didn't have this problem running Intrepid, btw.  Thanks in advance!

---

### Post by shrimpy89 on 2009-05-02
Bump

---

### Post by shrimpy89 on 2009-05-03
Bump

---

### Post by Don1500 on 2009-05-03
BUMP

Me Too

---

### Post by Don1500 on 2009-05-06
Bump

---

### Post by everettattebury on 2009-05-15
Try this:

Find the "handle" to the left of the taskbar and right click on it, then click "Preferences".  A Window should open titled "Window List Preferences".
Look at the first section titled "Window List Content" and make sure that the choice "Show windows from current workspace" is selected.  If the other choice, "Show windows from all workspaces" was selected, then that was your problem.  If selecting "Show windows from current workspace" doesn't fix it, then your problem is caused by something else.

---

### Post by shrimpy89 on 2009-06-09
Thanks for the reply (although mine is three weeks late).  I've checked that, so it's definitely a bug. Sometimes both panels disappear entirely when I switch.  I haven't seen anything like it on launchpad, so I'll file a bug report. I hope there's a solid fix for it.

---

### Post by I[AM]SMRT on 2009-06-10
I've been having the exact same problem ever since I upgraded to Jaunty.

---

### Post by shrimpy89 on 2009-06-24
Bump....I have personally seen this on multiple Ubuntu computers now.  Solutions, anyone?  The problem is definitely Compiz-related.

---

### Post by I[AM]SMRT on 2009-06-24
Have you filed a bug report yet?

---

### Post by shrimpy89 on 2009-06-24
I've already reported the bug to launchpad, although once everyone narrowed it down to a Compiz problem, there's been no more progress.  I don't yet know enough about the inner workings of Linux to tackle it myself.

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/385446](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/385446)

---

### Post by I[AM]SMRT on 2009-07-01
I found the solution:

[http://forum.compiz-fusion.org/showpost.php?p=48651&postcount=2](http://forum.compiz-fusion.org/showpost.php?p=48651&postcount=2)

---

### Post by shrimpy89 on 2009-07-01
> **'I[AM]SMRT said:**
> I found the solution:

[http://forum.compiz-fusion.org/showpost.php?p=48651&postcount=2](http://forum.compiz-fusion.org/showpost.php?p=48651&postcount=2)

It works! Thanks man

---

