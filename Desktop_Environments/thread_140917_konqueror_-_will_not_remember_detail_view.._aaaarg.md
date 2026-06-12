---
title: "konqueror - will not remember detail view.. aaaargh!"
date: 2006-03-07
forum: Desktop Environments
---

### Post by zi99y on 2006-03-07
It may seem like a minor thing, but I'm using KDE 3.5.1 - not the Kubuntu install but the Gnome package converted to KDE.

Anyway, I can't get konqueror to use the same detailed list view for every folder, I have saved ALL profiles with the view mode that I like, but when I change folders (usually to System) it ALWAYS reverts back to the regular icon types - which is totally user unfriendly to me.

Anyone help here? What I want is simple but I can't seem to find out how to do it, and I have looked through the konqueror manual too...

---

### Post by zi99y on 2006-03-09
After some investigation it turns out it's been a bug in konqueror since kde 3.4.1. [https://bugs.kde.org/show_bug.cgi?id=108542](https://bugs.kde.org/show_bug.cgi?id=108542)

Isn't that FASCINATING :mrgreen:

---

### Post by danvis on 2008-02-10
Hi!

Thanks a lot for the link to the bug report link. It helped me to fix this problem. Fortunately somewhere in the discussion a workaround is given that helped me to fix this nasty problem. It took some time to find it, so I state this solution hear once more.

In the link above Gerrit wrote:
...
Go to "Control Center" &#8594; "Kde Components" &#8594; "File Associations" &#8594; "media" and for "hdd_mounted", "hdd_unmounted", "nfs_mounted", "nfs_unmounted" and so on in the Embedding tab on the right side move "Detailed List View" to the top. That way you have always "Detailed List View"
You should also change "Control Center" &#8594; "Kde Components" &#8594; "File Associations" &#8594; "inode" &#8594; "directory" to Detailed List View
...

The radio button at the top has to be set to the lowest item.
The control center can be found in konqueror or by calling "kcontrol" in the bash.
Every things seems to be right now.

So long ...

---

