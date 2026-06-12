---
title: "Random No Borders in Firefox with Compiz Fusion/Emerald"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by Rockmaninoff on 2007-08-29
Hey all-

Sorry for clogging the forums with yet another Compiz Fusion post regarding no windows, but I've tried a number of things and they don't seem to work.

This all began when I was trying to update Tilda (which is another issue that I need help with...) to enable "true transparency."

I'm running Feisty Fawn on an nVidia graphics card with Compiz Fusion installed.  I also have the convenient Fusion Icon installed, and the options listed as:

Window Manager: Compiz
Compiz Options: Indirect Rendering [X]
Window Decorator: Emerald

 The problem is thus:

When I boot up Firefox, everything loads fine, the window borders pop up, and everything is dandy.  However, on certain webpages (for instance, when I did a Google search for "tilda transparency"), the borders disappear, and Firefox disappears from the bottom toolbar.  When I go back to a page that displays borders properly, the reappear, and Firefox pops up again in the toolbar.

Any suggestions?

Also, as an additional problem, I'm trying to patch Tilda to enable true transparency, but I don't really know how.  I'm completely new to Linux, but I'm trying to update it using the following patch file:

[https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/116224](https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/116224)

How could I do this?

Thanks!

---

### Post by el-mar01 on 2008-04-09
Sorry to bump this ancient thread but the problem still persists with Ubuntu 7.10 with Emerald.

---

### Post by tsphere on 2008-04-09
ditto. Happened to me many a times. have to restart FF and it usually helps.

---

### Post by ssteinbr on 2008-04-09
If you've made any changes to the window rules within Compiz Config Settings Manager, these may be the culprit.  For instance, lets say you have the rules set up so that any window with tilda in the title has no borders, skips the taskbar, etc so that tilda will have "true" transparency.  This means when you search for tilda in google, the title of the window that it returns will have "tilda" in the title.  Therefore, that window will have no borders and won't show up in the taskbar.

---

### Post by el-mar01 on 2008-04-10
> **tsphere said:**
> ditto. Happened to me many a times. have to restart FF and it usually helps.

My fix is to put your mouse over the minimise/maximise/close buttons .... also for the record I don't have the window rules plugin enabled and the problem still happens.

---

