---
title: "Stop Window Spread from showing All Workspaces / Desktops"
date: 2014-06-09
forum: Desktop Environments
---

### Post by xmbwd on 2014-06-09
I am on Ubuntu 14.04, stock.  I want the "Spread All Windows" function to operate like the Switcher and only show windows from the active workspace.  Right now, for some reason, it shows applications from both the active workspace and the adjacent workspace.

Here is what I've done so far:

[LIST]
[*]I have enabled Workspaces in Settings>Appearance>Behavior.
[*]I also have set the number of Workspaces in Unity Tweak Tool>Workspace Settings to 2 Horizontal by 1 Vertical; and the bottom left corner to be a "Spread All Windows" Hotspot -- and the upper right corner to be a "Show Workspaces" Hotspot.
[*]Finally, in CCSM I have set a program to only open in the second horizontal workspace via Windows Management>Place Windows>Fixed Window Placement.
[/LIST]

Does anyone know how to get the window spread to be limited only to the active workspace? 

Thanks.

---

### Post by mc4man on 2014-06-10
You have set your edge binding for the wrong scale option - "Initiate Window Picker For All Windows", ("Spread All Windows" in your tweak tool.
I don't use tweak tools but the one you want is shown in screen - "Initiate Window Picker"

---

### Post by xmbwd on 2014-06-10
_**Brilliant**_!  You are exactly right.  CCSM>Window Management>Scale>Initiate Window Picker>(select edge you prefer).  I had not set the spread from CCSM, but rather from Unity Tweak Tool -- and I couldn't identify those extra settings.

*Thank you so much*.  That was driving me NUTS.

---

