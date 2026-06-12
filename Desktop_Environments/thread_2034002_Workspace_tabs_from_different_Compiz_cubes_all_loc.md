---
title: "Workspace tabs from different Compiz cubes all located on single workspace"
date: 2012-07-27
forum: Desktop Environments
---

### Post by GammaPoint on 2012-07-27
Hi, I just installed Xubuntu and Compiz. In the Compiz settings, under General Options -> Desktop Size I set the number of horizontal desktops to 4 and the number of desktops to 4. So I can rotate around my desktop in a cube now. However, at the top right of my desktop (you know where it shows 4 boxes for each desktop) it only puts icons in the first box (which is always the compiz desktop I'm currently on). The other 3 boxes stay dark gray. 

Furthermore, if I have tabs and browsers open on all 4 desktops, I see the tab at the top for ALL of them simultaneously, regardless of whether they are on a different desktop or not. I'd prefer this not be the case and that I only see tabs for things that are open on that desktop because otherwise things get too cluttered. 

Anyone know how to fix this? I appreciate the help!

---

### Post by LewisTM on 2012-07-27
In CCSM, set the number of desktops to 1. The horizontal virtual size is enough to give you 4 workspaces (called viewports). 4 desktops x 4 viewports = 16 workspaces = trouble.

For the window buttons, go to your Panel configuration/Items tab and edit the Window Buttons item. Make sure 'Show windows for all workspaces or viewports' is unchecked.

Cheers!

---

### Post by GammaPoint on 2012-07-27
> **LewisTM said:**
> In CCSM, set the number of desktops to 1. The horizontal virtual size is enough to give you 4 workspaces (called viewports). 4 desktops x 4 viewports = 16 workspaces = trouble.

For the window buttons, go to your Panel configuration/Items tab and edit the Window Buttons item. Make sure 'Show windows for all workspaces or viewports' is unchecked.

Cheers!


LewisTM, thanks so much! You completely fixed my problem!

---

