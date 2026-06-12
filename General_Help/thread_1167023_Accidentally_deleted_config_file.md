---
title: "Accidentally deleted config file"
date: 2009-05-22
forum: General Help
---

### Post by banduan on 2009-05-22
I was attempting to delete alsa-base, and accidentally deleted alsa-base.conf instead, which was what I'd wanted to keep...

How do I get the original config back? Reinstalling Alsa-base did not work!:icon_frown:

---

### Post by Psycho.mario on 2009-05-22
In the folder that the config file was in, there might be an "alsa-base.conf~" remove the ~ from the name and it'll be fixed. OR it might be in your wastebasket (the icon at the bottom right of your screen)

If not, then i cant help you.

---

### Post by banduan on 2009-05-23
Thx!

While what you advised didn't work, in the process of following it I noticed that when alsa-base reinstalled it placed the config file as a newly dpkg'd file (probably because it conflicted with an existing file). I renamed the conflicteing files and while I never recovered the old file, I don't need to now (I think).

---

