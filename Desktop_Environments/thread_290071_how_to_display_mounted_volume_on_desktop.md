---
title: "how to display mounted volume on desktop"
date: 2006-10-31
forum: Desktop Environments
---

### Post by frankelr on 2006-10-31
How do I get a directory which I mounted to display as a volume icon on the destop? I mad my mount point /mnt. Some post seem to say that if you want a volume display you must use /media as a mount point? What is good practice when choosing adirectory for mount points.  The actual mount works fine and I can access the mounted partition.

Any help would be appreciated.

Bob

---

### Post by ciscosurfer on 2006-10-31
Use your /media directory if you want your 'volumes' to show up on the desktop.  If your other volumes are not showing up, you can make them show up by going into your Configuration Editor (Applications > System Tools > Configuration Editor), click apps > nautilus > desktop and then place a checkmark in the empty box labeled 'volumes_visible'.  As a sidenote, you can always make a bookmark to your mounted volume (whether you leave your mount point in /mnt or /media) from within Nautilus by going to your mounted directory, going to the top menu from within Nautilus, clicking Bookmarks > Add Bookmark (or CTRL-D) it will then show up on the left sidebar if you choose Places.  Hope that helps.

---

### Post by frankelr on 2006-10-31
Thanks for the help, I'll try it tomorrow, by this time my head is spinning

Bob

---

