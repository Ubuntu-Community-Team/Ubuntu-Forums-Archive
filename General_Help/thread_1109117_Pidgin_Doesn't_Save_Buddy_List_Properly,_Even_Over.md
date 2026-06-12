---
title: "Pidgin Doesn't Save Buddy List Properly, Even Overwrites root Files!"
date: 2009-03-28
forum: General Help
---

### Post by GenuineXP on 2009-03-28
I don't understand this one, but it seems it may be a very annoying bug. Pidgin rewrites my blist.xml file everytime it starts, reverting it to a previous state. The problem with this is that I have unfortunately had to block certain screen names. Whenever Pidgin restarts, all of the blocked screen names aren't blocked anymore! They disappear from blist.xml. I'll suddenly see these names log in on my buddy list and I have to manually block them again and again! Unacceptable.

One thing I tried was to block the names and check that they were written into blist.xml, then change the permissions of blist.xml so that Pidgin couldn't overwrite it. No luck. I even switched to root, took ownership of the file (root:root), and set the permissions to -r--r--r--. Nope. Pidgin still overwrote the file!

Has anyone else run into this issue? I'm hoping someone has found a workaround, as this is getting very frustrating. I like Pidgin, but I may have to ditch it if it keeps this up.

Thanks.

---

