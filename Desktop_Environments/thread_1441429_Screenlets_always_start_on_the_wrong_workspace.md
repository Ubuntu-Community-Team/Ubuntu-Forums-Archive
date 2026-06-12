---
title: "Screenlets always start on the wrong workspace"
date: 2010-03-28
forum: Desktop Environments
---

### Post by basher5_2 on 2010-03-28
I have 4 workspaces and the compiz cube enabled. I have perfect clock screenlet autostart on login but it doesn't start on the same desktop as when I logged out. It should be on Workspace 1 but starts on workspace 4.

---

### Post by JustinR on 2010-03-28
I have found that the screenlets package, along with gdesklets, don't work well. Deleted screenlets usually popped back up after restarting and the ones I saved never popped up! The gdesklets package had poor quality applications so that didn't work well either.

The only thing I would look at would be in Startup Applications or in (most probably) Gconf-editor - to figure out where Screenlets is placing it.

**Edit** : In Gconf-Editor I would most likely look in Apps > nautilus > desktop-metadata (where icon positions are stored on the desktop) to see if they're in there.

Or in, Apps > Screenlets, and see if anything is in there.

---

