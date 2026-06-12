---
title: "desktop switcher ... can it be faster?"
date: 2010-04-26
forum: Desktop Environments
---

### Post by Skaperen on 2010-04-26
Right now, the desktop switcher (Ctrl+Alt+<somearrowkey>) slides the windows around.  I'd like to eliminate the sliding effect and just jump all the way to the new desktop.

Also, everything is organized as a grid where movement by keyboard is one step at a time.  I'd like to do something like I did with text consoles long ago.  Normally text console switching is done by Alt+F<nn> or Ctrl+Alt+F<nn> and it takes you direct to the console (or the particular instance X if multiple are running).  On Slackware, I extended this by adding a new keymap and opening more console getty processes.  Alt+(one of many keys) or Ctrl+Alt+(one of many keys) goes to one of 63 different consoles.  I'd like to do something like that inside X to jump around to specific desktops.  Some other meta combination would be needed so Ctrl+Alt still switches consoles instead of desktops.  Then I can associate a desktop to a particular keyboard location, hold the meta combination and press that key, and be there in that desktop.

If the above the can be done without installing any new software, that would be most preferred.  If installing new software cannot be avoided, then not removing something already installed would be preferred.

---

### Post by steveneddy on 2010-04-26
Fast desktop switching with no effects can be accomplished by turning off Compiz.

*********

To get to a console, simply 

Crtl+Alt+F1 through F6

Crtl+Alt+F7 is X 

Ctrl+Alt+F8 is system stats

Hope that helps.

---

### Post by 3rdalbum on 2010-04-27
In(stall) compizconfig-settings-manager and turn off Desktop Cube, Desktop Wall and Rotate Cube. You'll get an instant desktop switch. Or, you could set the "wall sliding duration" to zero under the Viewport Switching tab of the Desktop Wall plugin.

---

### Post by SnickerSnack on 2010-04-27
In the CompizCongfig Settings Manager (you may need to install this), type "view" in the filter field, click on "Viewport switcher".  Find the tab labeled "Go to specific viewport".  Set up your shortcuts.

---

### Post by Skaperen on 2010-04-30
Setting the "wall sliding duration" to zero succeeded in getting an instant, instead of sliding, desktop switch.

I went to look for the other suggestion on shortcuts.  I could not find it in the first pass, so I was switching windows to come back to where the browser was open to ubuntuforums.org to view this thread again.  Just one desktop away from it, it froze hard.  The grid showing the 6x4 array of desktops stayed up, along with the array in the most recent position.  About every 5 seconds, the screen would flicker with some black.  After letting it be like this for about 2 minutes, I pressed Ctrl+Alt+F1 to get a text console.  I got that console.  But as I was typing to login, it went black.  I switched back to Ctrl+Alt+F7 and the entire screen was all white, except for the I-beam icon for the mouse point.  Mouse movements worked OK.  I switched back to Ctrl+Alt+F1 and the screen was now garbled (like X not restoring video buffer contents after a successful mode change).  I switched around to other text consoles, and they each had different garbage, except F8 did have displayed test (so definitely the video mode had been changed back to text correctly).  I went back to F7 and played around and noticed that moving the mouse around triggered some changes in it's icon. Pressing mouse buttons brought up menus (still on that all-white background). So X was indeed alive, and windows were present, and buttons could be acted on.  But I could not see anything but new stuff being put on the screen.  Then I noticed that desktop switching was also working, but the grid never showed up.  Then I noticed that ONE window in ONE desktop was visible.  I believe that window was highest in the window stack, because it was one of two which were set "always on top", and it was the 2nd one set that way (so it was probably above the other one).

I was able to do a logout (poked around and found the invisible button for it). Now the display looked fine.  Log back in and all looks fine.  I shut down, anyway, just to be sure all video card state was back to default.

Any idea what went wrong?  One point: the CompizConfig Settings Manager window was up and in the Desktop Wall submenu, when I did that switching that froze.  I just did that again and this time no freeze.  Maybe it can just freeze sometimes and maybe only in that state (having just changed stuff and/or with a zero duration).  The zero duration setting was successfully saved and is still in effect.  I may try other things, later.

I still have not found where to set a specific key combination to go to a specific desktop.  I'd like to do Ctrl+Alt+(any letter or number or punctuation) each bound to a different desktop.  I'll keep looking.

---

