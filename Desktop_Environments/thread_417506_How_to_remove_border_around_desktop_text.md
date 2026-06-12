---
title: "How to remove border around desktop text"
date: 2007-04-21
forum: Desktop Environments
---

### Post by Foxman2k on 2007-04-21
In edgy,  I did not have borders around the text on the desktop for icons.

In feisty,  I do.

How do I remove these?

See the attached screenshots...

---

### Post by Foxman2k on 2007-04-21
Anyone?  This must be a simple config change?

---

### Post by yabbadabbadont on 2007-04-21
What happens if you single left-click somewhere on the desktop?  Just on the background, not on any icons or anything.

---

### Post by Foxman2k on 2007-04-22
Nothing, icons remain the same. The border is still there.

---

### Post by Foxman2k on 2007-04-22
Here is a screenshot,  see how all the icons' text have the border around them?

---

### Post by yabbadabbadont on 2007-04-22
Disable Beryl and see if it reverts to the normal behavior.  It might be a Beryl option that you can change.  You might also run gconf-editor  (I think it is listed as the configuration editor in Applications->System Tools) and browse down to the nautilus settings under apps.  There might be some new nautilus option you can change.  Finally, you might try using a different theme and see if it changes.  Since I'm not sure what is causing it, I'm just listing all the different things that I think might be able to cause it.  :)

---

### Post by mcduck on 2007-04-22
Have you added some settings for desktop icons into your ~/.gtkrc-2.0 file? I noticed the same problem, "NautilusIconContainer::normal_alpha = 0" doesn't work in Feisty so setting color for desktop icons without having the border around icon text doesn't seem to be possible any more..

---

