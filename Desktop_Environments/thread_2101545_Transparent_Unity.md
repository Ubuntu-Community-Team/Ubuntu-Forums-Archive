---
title: "Transparent Unity"
date: 2013-01-04
forum: Desktop Environments
---

### Post by bman on 2013-01-04
So I am using Unsettings to tweak stuff, and I can get the top panel 100% transparent, but the Unity Dash does not. It becomes a white, or just very close to 100%.

Anyone get it 100% transparent?

---

### Post by mc4man on 2013-01-05
In 12.04 probably not unless you patch unity to allow using black as a custom color. Then by setting the 'custom color' opacity to at least the min of 2 with black will produce a 'pretty much' transparent launcher. Opacity in custom color doesn't affect the launcher after 2,  - screens, though it does affect the Dash. -  
(here atm I use a high opacity & a no blur Dash with black on 13.04

12.10 & 13.04 do again allow black as a custom color, though for the moment prefer plank over unity launcher, just exposing for example screen

---

### Post by mc4man on 2013-01-05
Here's the bug I had on black, maybe it's fixed in 12.04, maybe not
[https://bugs.launchpad.net/unity/+bug/924586](https://bugs.launchpad.net/unity/+bug/924586)

---

### Post by bman on 2013-01-05
> **mc4man said:**
> In 12.04 probably not unless you patch unity to allow using black as a custom color. Then by setting the 'custom color' opacity to at least the min of 2 with black will produce a 'pretty much' transparent launcher. Opacity in custom color doesn't affect the launcher after 2,  - screens, though it does affect the Dash. -  
(here atm I use a high opacity & a no blur Dash with black on 13.04

12.10 & 13.04 do again allow black as a custom color, though for the moment prefer plank over unity launcher, just exposing for example screen

With the UNsettings program and others, I do select black as the color and set it to very low, but I always end up with a color difference then what my desktop is.

I don't get how you accomplished that.

This is the best I came up with.

---

### Post by mc4man on 2013-01-05
What ubuntu release are you using?

---

### Post by bman on 2013-01-05
12.04.

I am just saying those tweaking programs allow you to use black, but makes no difference.

---

### Post by mc4man on 2013-01-05
give me about 5 min or so to dl the 12.04.1 iso & I'll boot to a live 12.04 session & see whats up...
(I only use ccsm (compizconfig-setting-manager) to adjust compiz/unity

---

### Post by mc4man on 2013-01-05
So on  12.04 with the default unity you can **not use black**. I'd guess your tweaking apps make it look like you can but it's not happening.

If you actually did use black, (with ANY opacity), you'd run into the bug I linked. None of your launcher icons would be visible.

screen shows what would happen.

You have 5 choices - 
Forget about it
Wait for the fix to be backported to 12.04, don't hold your breath there though there is no  reason it can't be.
Hope someone includes the fix in a 12.04 unity ppa build
Build unity yourself with a patched source
use 12.10 or 13.04, (now or later

Edit: just so it's clear - the ccsm setting for this is "Background Color". It affects the tinting but not the opacity of the launcher, also it  doesn't take affect unless any opacity is set for "Background Color" as in screen (2

---

### Post by bman on 2013-01-05
Thanks for trying it out.

Yea I guess I will have to deal with it for now :)

---

### Post by mc4man on 2013-01-05
Well I posted a new comment in my bug, we'll see if there is any constructive response 
(it would need an SRU which can be a pita

If you get inclined it's not that hard hard to rebuild a unity package set, probably take about 1/2 hr. or less. So post a request here if that day arises & I'll give you a simple copy & paste to follow.

---

