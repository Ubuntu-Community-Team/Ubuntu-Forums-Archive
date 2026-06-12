---
title: "How to add keyboard layout switcher to the panel?"
date: 2009-07-05
forum: Desktop Environments
---

### Post by DjDarkman on 2009-07-05
Hello, I am using UNR on a netbook and need the keyboard layout switcher on the panel badly, but I can't find a way to do it. How can I add that applet to the UNR panel?

---

### Post by CinemaFoto on 2009-08-28
It is three months later after the previous post and nobody still didn't find any solution for Keyboard Layout Indicator Applet on UNR Desktop Panel? Hope it is not true.
I still can switch to regular Ubuntu desktop, but... In contrary to many opinions I found UNR desktop interesting and the only annoying thing is automatic maximization of every opened window.
Anyway, has the problem of the Keyboard Layout Indicator (Switcher) Applet any solutions?
Thank You in advance.

---

### Post by Thomas_G on 2009-08-28
There's a neat workaround available described by Alan Hogue:
[http://alanhogue.blogspot.com/2008/12/adding-applets-to-ubuntu-netbook-remix.html](http://alanhogue.blogspot.com/2008/12/adding-applets-to-ubuntu-netbook-remix.html)

Good luck!

Thomas

---

### Post by CinemaFoto on 2009-09-04
Thank You very much! It was very useful and simple. Thank Alan Hogue for his blog.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Proud user of Linux Ubuntu NBR on Asus eeePC 1005HA
Proud user of Linux Ubuntu 9.04 on Intel Pentium III 1GHz based computers

---

### Post by wayeast on 2009-11-17
CinemaFoto, I am experiencing the same frustration with getting the keyboard switcher onto UNR.  I looked at Alan Hogue's blog page linked above, but don't know how to use his workaround for the keyboard switcher applet. That is, it seems his suggestion is only good for adding applets for applications listed in the main menu.  This is not the case for something like the keyboard switcher.  Is it?  Would you (or anyone else) kindly explain why I can't do this?  Thanks.

---

### Post by wayeast on 2010-03-11
This thread is ancient, but for anyone who might stumble across it with the same problem, I've found the solution (at last) to my problem (as indicated in my last post, the linked blog entry above didn't address my particular problem).

For those who want to add applets to the panel (such as the keyboard layout switcher) of a standard UNR 9.10 Gnome desktop, first right-click on the open panel (black strip at the top of the screen) and select "Remove from panel."  After that, you can again right-click in the same space and select "Add to panel" to add any applet you like from the Gnome desktop.

As near as I can tell, this works this way because what appears to be the panel on an out-of-the-box installation is actually a working applet called Window Picker (you can find it in the "Add Applet" dialogue box).  You must first remove this before you can get to the real panel and start adding other applets.  Don't forget, though, once you've added the applet(s) you want (in my case, the keyboard switcher) and moved it/them into the desired location on the panel, to add either Window Picker or one of the other window selectors back to your panel.  Otherwise you won't be able to see your running applications at all!

For those who figured this out long ago (including Alan Hogue, if I missed something important in that link) many apologies for the repetition.  If this helps somebody somewhere, so much the better...

---

### Post by Moshanator on 2010-03-22
This issue gets even more problematic in Lucid, where [panel customization is disabled for sake of user experience]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-netbook-remix-default-settings/+bug/448109/comments/8"). That means the current workaround will not do anymore.

EDIT: No workaround is needed in Lucid. The layout switcher has moved to the notification area and will be visible whenever there are layouts to switch between.

---

### Post by mike-g2 on 2010-09-13
I'm running a std. version of Lucid, but i don't have any keyboard/layout indicator applet nor can I find when searching the predefined applets when right clicking on the panel.  Could you tell me where you found it?

---

### Post by Moshanator on 2010-09-14
As said, the indicator will appear if there are two or more layouts to choose from. Go to System - Preferences - Keyboard Settings, add your needed layouts and the indicator will appear automatically on the notification area. Also, when posting in a thread, check the date of the last post.

---

