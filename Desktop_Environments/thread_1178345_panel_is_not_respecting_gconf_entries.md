---
title: "panel is not respecting gconf entries"
date: 2009-06-04
forum: Desktop Environments
---

### Post by Nycticorax on 2009-06-04
I was in the middle or reporting a bug in the workspace_switcher panel applet (#383641), and I thought it would be a good idea to try with fresh gconf settings. So I renamed ~/.gconf and logged out and back in. After confirming that the bug was still present I reverted the rename and logged out and back in. 

Now I have lost all my panel settings, and am having difficulty recreating them. However they are all there in the /apps/panel subtree of gconf, but they are not being respected by the panel that appears. For example /apps/panel lists all the applets that were there, despite none being actually present. And if I make changes in /apps/panel they have no effect.

How can I get my previous panel back / force my panel to respect the entries in gconf /apps/panel?

Additionally, is this a bug, or was renaming ~/.gconf a stupid thing to do?

Thanks a lot.

---

