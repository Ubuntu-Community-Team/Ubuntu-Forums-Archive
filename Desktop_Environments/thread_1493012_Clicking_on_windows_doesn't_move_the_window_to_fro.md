---
title: "Clicking on windows doesn't move the window to front"
date: 2010-05-25
forum: Desktop Environments
---

### Post by roytang on 2010-05-25
Hi,

I'm not sure whether this is intended behavior or not. Let's say I have two windows A and B open unmaximized such that their area overlaps with A in front. If I click window B it gets the focus as I expect, but window A stays on top of it. All my keyboard events get sent to window B correctly, but I need to click on the title bar for it to appear on top of window A. Switching windows using Alt+TAB or taskbar click works as I expect - window B will appear on top.

I encountered this in 10.4, not sure if it was there before or I only noticed it now.

Any idea? Is this a bug or some setting somewhere I need to adjust?

---

### Post by tom4everitt on 2010-05-25
It sounds like a bug. On my (fresh install) 10.04 it does work as you expect it to: windows are always becoming focused and in front upon click.

---

### Post by roytang on 2010-05-26
Hm, you're right. I have a clean 10.04 install in a VM and it's working correctly there.

Any idea what settings/config files I could check to figure out this behavior?

On the problematic machine (my laptop), it was an upgrade from the previous version (Karmic) instead of a clean install of Lucid, would that matter?

---

### Post by roytang on 2010-05-26
Found the problem...needed to enable auto raise and raise on focus in metacity general settings.

---

