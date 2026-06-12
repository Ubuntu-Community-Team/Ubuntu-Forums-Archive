---
title: "firefox has two different full screen modes?"
date: 2009-04-28
forum: Desktop Environments
---

### Post by Roger E Critchlow Jr on 2009-04-28
Firefox has two different full screen modes.

One is toggled by F11.  The window borders and title bar go away and you have the Firefox UI inside a full screen window.

The other is entered by selecting View > [ ] Full Screen from the menus.  (This menu entry is misleadingly labeled with the accelerator F11, don't believe it)  This mode is exited by clicking the [un full screen] icon next to the window close X in the upper right corner of the full screen UI.

In this second mode, the window borders, the title bar, the menu bar, and the bookmarks toolbar all go away.  Furthermore, the navigation toolbar and the tabs selector scroll off screen when the mouse is not near the top of the screen.  So you actually get a full screen for the application running in your currently selected tab, but you can get to another tab or back to normal mode if you like.

If you try to use F11 to exit the View > Full Screen mode, you get into a third mode where the window borders and title bar are restored, but the menu bar and bookmarks toolbar are still gone, and the navigation toolbar and tabs selector still scroll off window.  

It seems that F11 was supposed to implement the same full screen mode that the View menu implements, but somehow it got sidetracked into implementing the usual gtk full screen mode instead.

Some threads made me suspect that this was a compiz problem, but I see the same behavior whether I have Visual Effects enabled or not.

I think this is probably a bug, and that the gtk full screen mode should be scrapped in favor of the true full screen mode implemented by the View menu.

Can anyone confirm this?

-- rec --

---

### Post by inearlygaveup on 2009-04-29
Thanks for that info - I was confused as well.

Mine keeps changing to Full Screen on its own, so its good to know about the [un full screen] saves me doing F11 x 3 taps.

Does anyone knows how to stop the change happening on its own

---

### Post by lisati on 2009-04-29
I don't see any difference on my machine.

---

### Post by chaceos on 2012-04-07
> **Roger E Critchlow Jr said:**
> Firefox has two different full screen modes.

One is toggled by F11.  The window borders and title bar go away and you have the Firefox UI inside a full screen window.

The other is entered by selecting View > [ ] Full Screen from the menus.  (This menu entry is misleadingly labeled with the accelerator F11, don't believe it)  This mode is exited by clicking the [un full screen] icon next to the window close X in the upper right corner of the full screen UI.

In this second mode, the window borders, the title bar, the menu bar, and the bookmarks toolbar all go away.  Furthermore, the navigation toolbar and the tabs selector scroll off screen when the mouse is not near the top of the screen.  So you actually get a full screen for the application running in your currently selected tab, but you can get to another tab or back to normal mode if you like.

If you try to use F11 to exit the View > Full Screen mode, you get into a third mode where the window borders and title bar are restored, but the menu bar and bookmarks toolbar are still gone, and the navigation toolbar and tabs selector still scroll off window.  

It seems that F11 was supposed to implement the same full screen mode that the View menu implements, but somehow it got sidetracked into implementing the usual gtk full screen mode instead.

Some threads made me suspect that this was a compiz problem, but I see the same behavior whether I have Visual Effects enabled or not.

I think this is probably a bug, and that the gtk full screen mode should be scrapped in favor of the true full screen mode implemented by the View menu.

Can anyone confirm this?

-- rec --


I have exactly the same problem! I'm so happy I found another human being tormented by this!

I use lucid, before the upgrade made available for Firefox 9 (or 10?) F11 was exactly the same as View--> Fullscreen. Now F11 is not equal to View ---> Fullscreen.

View---> Fullscreen is Fullscreen. But F11 does only hide the title bar of Firefox window. Of course F11 was a very useful shortcut and of course not having a full screen is more preferable than going every time to View---> Fullscreen.

Can anyone enlighten me?

---

### Post by dniMretsaM on 2012-04-07
NVM, old thread.

---

### Post by uRock on 2012-04-07
If you are having these issues, then please start a new thread.

Thread Closed

---

