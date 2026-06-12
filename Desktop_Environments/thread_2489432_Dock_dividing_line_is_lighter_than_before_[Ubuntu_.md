---
title: "Dock dividing line is lighter than before [Ubuntu 22.04.2]"
date: 2023-07-30
forum: Desktop Environments
---

### Post by peterx14 on 2023-07-30
Call me pedantic, but I note that the dividing line on the dock is a little lighter than it was previously:
[ATTACH=CONFIG]292523[/ATTACH]

Previously the dividing line was #595156 (maybe it's semi-transparent though so that might be the background), and now it's #c7c7c7 which is loads brighter! I can't be certain, but I believe this change happened fairly recently.

I'd already noticed that the Open File dialogue in Audacious didn't look the same as before... but to be fair, it always looks a bit weird and it still works and it only affects a single app so I'd ignore it. But it seems like it might be affected by the same recent changes? The Audacious settings dialogue is pretty hilarious these days, but to be fair, I pretty much never look at that dialogue... and I am running Audacious in legacy GTK mode so, I'm really only presenting this image for comedy value!! :P
[ATTACH=CONFIG]292524[/ATTACH]

Just to be clear, none of these changes are really an issue to me. I dislike things suddenly changing, so I'd be interested in knowing if these changes were intentional, but I'm otherwise resigned to just getting on with it as-is.

---

### Post by peterx14 on 2023-07-30
Found another issue; when I scroll right into a workspace with an active application (terminal in this case), the active application is indicated with a light-ish, rounded corner, box. I continue to scroll right to the next empty workspace, and then scroll back to the previous workspace and... the light-ish, rounded corner box fails to render correctly. (Image shows correctly rendered (left), and incorrectly rendered box (right)).
[ATTACH=CONFIG]292525[/ATTACH]

---

### Post by peterx14 on 2023-07-31
Aaaand another minor issue; when I ctrl-alt-t to open a new Terminal window, it used to appear in the top-left, and now it does, but it leaves a few pixels of gap* between it and the top panel.

*looks like 4px of top-gap.

---

