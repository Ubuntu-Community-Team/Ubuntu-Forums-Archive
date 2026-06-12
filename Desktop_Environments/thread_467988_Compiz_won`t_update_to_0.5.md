---
title: "Compiz won`t update to 0.5"
date: 2007-06-08
forum: Desktop Environments
---

### Post by orange2k on 2007-06-08
Today I saw my system being upgraded to 0.5 Compiz...
But I had some problems with my computer, so I reinstalled Feisty, but now Compiz still shows version 0.36 not 0.5. What can I do to get the latest version?

edit: now Ive noticed I posted in the wrong forum, perhaps a mod can move it into the right one?

---

### Post by dannyboy79 on 2007-06-08
> **orange2k said:**
> Today I saw my system being upgraded to 0.5 Compiz...
But I had some problems with my computer, so I reinstalled Feisty, but now Compiz still shows version 0.36 not 0.5. What can I do to get the latest version?

edit: now Ive noticed I posted in the wrong forum, perhaps a mod can move it into the right one?

That's weird, I don't see an update for it yet? When I do
sudo aptitude show compiz
it still shows 0.36. It's possible that they retracted it from the repo's after realizing something. Just be patient unless you know for sure that it should be available. THen if that's the case, you probably know where to download the 0.5 source files and compile it yourself if you don't want to wait for the binaries from the repo's.

---

### Post by orange2k on 2007-06-08
Well it was there this morning, but I guess it`s like you said...
They`ve probably realized that they should go with 0.4 (stable) instead of 0.5 (last unstable)...

---

