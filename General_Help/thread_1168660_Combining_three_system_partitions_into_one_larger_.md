---
title: "Combining three system partitions into one larger partition?"
date: 2009-05-24
forum: General Help
---

### Post by Pipps on 2009-05-24
I have the following partitions comprising my Linux installation:
- /boot on sda2, 
- swap on sa3
- /home on sda4

How may I combine /boot, swap and /home, together into one larger partition?

---

### Post by jonathanysp on 2009-05-24
why do you want to do that? its always good to have /home as another partition so when you reinstall another distro or update all your settings and files will stay there which is really useful when you update every few months

Is it because you want more space on /home? You can put /boot back into the / (root) partition but swap has to be on its own (some people say you dont really need swap unless you hibernate...idk) but its gonna be a pretty big operation shifting partitions around.

---

