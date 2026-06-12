---
title: "Mod-P not bound at startup in XMonad Gnome"
date: 2013-06-27
forum: Desktop Environments
---

### Post by lmullen on 2013-06-27
I've set up Xmonad with Gnome using the standard packages in the Ubuntu repository. I only have one custom Xmonad configuration file, xmonad.hs, which I've included below. When I login, Mod-P is not bound to the Gnome application launcher, as it should be. In order to get Mod-P to launch applications, I have to run the command ```
xmonad --restart
```. After that it works fine.

This problem is similar to the [thread here]("http://stackoverflow.com/questions/13965699/xmonad-dmenu-not-launching-spawning-on-startup"), except he was using dmenu instead of the the Gnome application launcher, and it doesn't seem like the problem was solved.

What should I do?

Here is my xmonad.hs; it's pretty standard.

```
import XMonad
import XMonad.Config.Gnome
import XMonad.Util.EZConfig
import XMonad.Hooks.ManageHelpers

main = xmonad $ gnomeConfig {       -- We use gnome rather than default
      modMask = mod4Mask            -- Use super key for mod
    , workspaces = myWorkspaces
    , manageHook = myManageHook 
   } `additionalKeysP` myKeys

myWorkspaces = ["1", "2", "3", "4", "5", "6", "7", "8", "9:web"]

myKeys = [
  -- Instead of killing window manager, log out
  ("M-S-q", spawn "gnome-session-quit") 
  ] 

myManageHook = composeAll [
    manageHook gnomeConfig
  , (className =? "Gnome-panel" <&&> title =? "Run Application") --> doCenterFloat
  , (className =? "sublime-text-2" <&&> title =? "Open File") --> doCenterFloat
  , (className =? "Empathy") --> doFloat
  , (resource =? "Dialog") --> doFloat
  ]


```

---

### Post by kevang2 on 2013-08-20
Same problem here with Ubuntu 12.04 and this xmonad.hs: [https://github.com/texttheater/.xmonad/blob/master/xmonad.hs](https://github.com/texttheater/.xmonad/blob/master/xmonad.hs)

---

### Post by kevang2 on 2013-08-23
I found a workaround. Adding the Win+p key binding directly works for me without restarting xmonad. My modified xmonad.hs is here: [https://github.com/texttheater/.xmonad/blob/master/xmonad.hs](https://github.com/texttheater/.xmonad/blob/master/xmonad.hs)

---

### Post by kevang2 on 2013-11-27
> **kevang2 said:**
> I found a workaround. Adding the Win+p key binding directly works for me without restarting xmonad. My modified xmonad.hs is here: [https://github.com/texttheater/.xmonad/blob/master/xmonad.hs](https://github.com/texttheater/.xmonad/blob/master/xmonad.hs)

I may have tricked myself into believing that this works, on further inspection it seems it doesn't. Sorry.

In other news, I didn't have this bug in Ubuntu 13.04 on my home machine, but since I upgraded to 13.10 it appeared there as well. :-x

---

