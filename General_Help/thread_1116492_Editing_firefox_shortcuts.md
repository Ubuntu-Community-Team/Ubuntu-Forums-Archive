---
title: "Editing firefox shortcuts"
date: 2009-04-05
forum: General Help
---

### Post by sideaway on 2009-04-05
Just wondering, firefox appear (and mention on their site) to not support editing of keyboard shortcuts.

I REALLY like using my backspace button as a back button - it appears I can't on linux FF. I pretty much use it for nearly every program with a GUI that I can. Is there a way to manually edit the back button shortcut? If so, what tools will I need for the job apart from gedit?

I'm sure there is... come on open source!

---

### Post by Tim Sharitt on 2009-04-05
Enter ```
about:config
``` into the firefox address bar and change the value for ```
browser.backspace_action
``` to 0. That should make backspace act as a back button.

---

### Post by sideaway on 2009-04-05
Thanks heaps, that worked brilliantly!

Ahhh, relief.

---

