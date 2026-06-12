---
title: "what happened to desktop switcher ?"
date: 2010-04-28
forum: Desktop Environments
---

### Post by Skaperen on 2010-04-28
I have my desktop switcher set up for 24 desktops. The grid is organized as 6 wide by 4 high.  It has worked well for months on 9.10.  However, a few days ago something strange happened.  I had walked away for a while and the screen saver kicked in.  That is something I've done many times with no problems before.  I came back and entered my password into the prompt.  This one time, something very strange happened.

Every window on all desktops were suddenly collected on just one desktop.  The 6x4 grid of desktops was gone.  Now there was just a row of boxes on the lower bar as if I had configured the desktop switcher to 24x1.  I could not access anything in X, as there was such a mess, and new windows would not even show up in front.  Alt+Ctrl+F1 got me to a text console where I could login as root and do a clean shutdown.  When it came back up, all was well.

I suspect something died of a rare line of bad code or maybe a memory allocation failure.  Has anyone seen this happen before?

---

