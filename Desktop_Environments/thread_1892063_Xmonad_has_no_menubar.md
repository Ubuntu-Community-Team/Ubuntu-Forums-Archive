---
title: "Xmonad has no menubar"
date: 2011-12-07
forum: Desktop Environments
---

### Post by wsubt on 2011-12-07
I use xmonad, 

manageHook = composeAll [
        -- other hooks,
        manageDocks
        , className =? "Unity-2d-panel"    --> doIgnore
        , className =? "Unity-2d-launcher" --> doIgnore
          -- more hooks
        ]

but there's no menubar. 
How can I fix it.

---

