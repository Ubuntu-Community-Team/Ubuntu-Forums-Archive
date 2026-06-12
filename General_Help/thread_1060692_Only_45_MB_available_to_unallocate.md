---
title: "Only 45 MB available to unallocate???"
date: 2009-02-05
forum: General Help
---

### Post by Aggression on 2009-02-05
I run Vista and am trying to unallocate some of what Vista is using so I can install Ubuntu.  Only problem?  When I go to shrink the C: drive's volume (which currently has 95GB free) it says that it says "Size of available shrink space in MB: 45"

[IMG]http://i116.photobucket.com/albums/o28/marshall_fehlendseele/allocated.jpg[/IMG]

Any ideas on how to fix this would be greatly appreciated.

---

### Post by Yellow Pasque on 2009-02-05
I don't know too much about Windows these days (I broke my Microsoft chains a couple years ago), but I will suggest the obvious:
Make sure your Windows volumes are chkdsk'd and defragged, and use a LiveCD with Gparted (like Ubuntu LiveCD) to resize partitions.

---

### Post by Aggression on 2009-02-05
I figured a defrag would be worth trying but was just making sure there wasn't anything else I could do for it.  Thanks for the help!

---

### Post by Elfy on 2009-02-05
If you still have problems you can try turning off the pagefile and hibernation if you use it, turn them on again once you've finished installing.

---

### Post by mcduck on 2009-02-05
..and run the defrag in Windows safe mode, that way as little as possible things are running so most of the files should be unlocked.

---

