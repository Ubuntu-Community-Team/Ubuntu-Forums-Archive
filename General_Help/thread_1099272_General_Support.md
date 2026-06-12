---
title: "General Support"
date: 2009-03-18
forum: General Help
---

### Post by nikola43 on 2009-03-18
I just used Proshield and answered yes to allow it to run a backup, which creates a tar file in a folder in the filesystem-it appears to have worked fine. Proshield recommends that this file be copied to another drive, which I intended to do, but when I went the Backup folder to copy it, an error pops up which says I don't have permission to see it. Well, that's fine too, since I'm a user, but I'm also the admin, so how do I get to see this file when the box that pops up doesn't include a place to put my password in?

---

### Post by adult swim on 2009-03-18
if you want to do it with gui press alt+f2 and enter in ```
gksu nautilus
``` you should be able to drag/drop
if you want to do it command line run ```
sudo cp /path/to/tar.gz /path/to/external
```

---

### Post by nikola43 on 2009-03-18
> **adult swim said:**
> if you want to do it with gui press alt+f2 and enter in ```
gksu nautilus
``` you should be able to drag/drop
if you want to do it command line run ```
sudo cp /path/to/tar.gz /path/to/external
```
Ok, so what does "gksu nautilus" do-what should I see?

---

### Post by adult swim on 2009-03-18
it should open a file browser (nautilus) that has root priveleges where you have the permissions to move any file

---

