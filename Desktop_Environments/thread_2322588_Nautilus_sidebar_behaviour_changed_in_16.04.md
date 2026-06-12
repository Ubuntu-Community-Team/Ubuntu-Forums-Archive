---
title: "Nautilus sidebar behaviour changed in 16.04"
date: 2016-04-29
forum: Desktop Environments
---

### Post by Briga on 2016-04-29
I wonder if this happens to me only and also if it is a wanted behaviour or not (to me isn't a good thing). 

In 14.04 when I have a nautilus window open I could drag a file over the sidebar on the left, let's say Pictures, after a second or so the right pane will switch to that location (Pictures) and I could keep on my drag & drop. 
Since I moved to 16.04 that is not happening anymore. If I drag something over a sidebar location the right pane won't change. I can still drop to that location (i.e. Pictures) but only on the sidebar. 
I find this less practical then before. 
Is it the same for everyone?

---

### Post by grahammechanical on 2016-04-29
It is the same for everyone. The Gnome developers have their own ideas about how their utilities should work and have been changing a lot of things during the last two years and no doubt there will be more changes to come as Ubuntu brings in more of Gnome 3.18 and then moves on to Gnome 3.20.

In fact we should be using Gnome Files 3.18 but something about it really did not work correctly and Ubuntu 16.04 reverted back to using Gnome Files 3.14.3. So, this behaviour has been in Gnome Files in Ubuntu for more than a year. I am not fussed about it myself.

---

### Post by mc4man on 2016-04-29
Initially there were 4 DnD open folder on hover - canvas view, sidebar, breadcrumb, list view. 
The canvas view was ill-advised & eventually reverted (or made a hidden option in 3.18+
The sidebar one was done away with [for some gtk3 reason]("https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1517656"), the other 2 are still active.

---

### Post by Briga on 2016-04-30
Thanks both for the explanation, I tried to google it but couldn't find it (poor choice of keywords I guess) and I was thinking it was affecting only me, since it didn't make any sense as a wanted behaviour.
I'll file it under "nonsense regressions" :) for now and when I'll have time see if I am able to fix it. Or hopefully someone will do it before :) :) :)

Take care.

---

