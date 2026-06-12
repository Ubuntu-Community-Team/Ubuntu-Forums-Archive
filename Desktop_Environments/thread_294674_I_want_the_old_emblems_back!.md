---
title: "I want the old emblems back!"
date: 2006-11-07
forum: Desktop Environments
---

### Post by abovett on 2006-11-07
Anyone else agree with me that the new emblems in nautilus are pretty pointless? They all look the same! I don't use them much but I like them to stand out for easy visual "keying" of important folders so I can spot them quickly - the new ones are useless for that.

Does anyone know a quick and easy way to get the old ones back? I mean instead of adding them each one by one?

Disappointed to see that asthetics is beginning to take preference over functionality in some areas of Ubuntu :(

Andy B

---

### Post by aidanr on 2006-11-07
personnally i like them a lot better, it shouldn't be too hard to replace them, just replace the icons in /usr/share/icons/human/scalable/emblems with the ones in /usr/share/icons/gnome/scalable/emblems i think that should work but back up the emblems folder your replacing just in case

---

### Post by abovett on 2006-11-07
> **aidanr said:**
> personnally i like them a lot better,Each to his own I guess. Obviously some people agree with you or they wouldn't have made the change. I don't get it though - what do you use them for? I use them for spotting essential folders at a glance - much the same as with any other icons - using shape and colour to enable me to quickly pick out the one I want. The new ones don't work for that purpose as they all have the same shape and colour - they don't give any speed advantage when looking for a folder.


> it shouldn't be too hard to replace them, just replace the icons in /usr/share/icons/human/scalable/emblems with the ones in /usr/share/icons/gnome/scalable/emblems i think that should work but back up the emblems folder your replacing just in case
That did it for some of them - thanks. I think there are a few more elsewhere that I'll have to track down but knowing where to look helps.

Cheers

Andy

UPDATE:

I found a (for me) better way - the relevant image files can be copied to ~/.icons/hicolor/scalable/emblems, or to ~/.icons/hicolor/48x48/emblems for the others I was missing. That way there's no need to mess with the originals outside the home directory. Only one wrinkle - they don't work if they share a name with an existing emblem so I had to rename all the files. I now have the old _and_ the new emblems without messing around with the files owned by root.

---

