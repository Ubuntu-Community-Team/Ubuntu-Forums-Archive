---
title: "indirect rendering at start up when running compiz"
date: 2008-01-25
forum: Desktop Effects &amp; Customization
---

### Post by Pathfinder_ on 2008-01-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/137388](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/137388) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				First off, I have ati radeon 9000 pro with the open source radeon driver. if I have compiz turned off then when the computer starts direct rendering is always on. However, once i start compiz and run glxinfo it shows "direct rendering: No (LIBGL_ALWAYS_INDIRECT set)". 
I don't know why it is set, but if I unset in the terminal to get direct rendering everything works more smoothly. 
My guess that for some reason compiz is setting like that. I've messed around w/ the compiz launcher in /usr/bin but I'm not a programmer so i didn't manage to resolve the issue. Hence I'm here asking if anybody has a similar problem and/or if anyone knows a solution besides manually unsettling it after I log in. 

Looks like someone posted a similar problem on launchpad

---

### Post by Pathfinder_ on 2008-01-27
bump

---

