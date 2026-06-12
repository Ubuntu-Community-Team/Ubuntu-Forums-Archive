---
title: "how do I use gvfs-fuse in Hardy ?"
date: 2008-05-01
forum: Desktop Environments
---

### Post by anando on 2008-05-01
Hi guys

I have been mounting a remote FS using the sshfs command. I have been told that in Hardy I could use the gvfs-fuse hooks (whatever *that* means) instead. 

Could someone point me to a document or else give me some basics as to how I could go about doing that ?

I use sshfs quite extensively, so any pointers will be hugely appreciated.

Thanks,
Anando.

---

### Post by olejorgen on 2008-05-01
Why not continuing to use sshfs?

Sorry I can't answer the question. I tried a little, but couldn't find a easy way. My guess is that it's hidden somewhere. Gnome style.

---

### Post by Awalton on 2008-05-02
sudo apt-get install gvfs-fuse
Then either mount your SSH share in nautilus or (if you have gvfs-bin installed, use gvfs-mount). Fuse shares for mounted GVFS file systems show up in ~/.gvfs/.

---

### Post by anando on 2008-05-07
> **olejorgen said:**
> Why not continuing to use sshfs? 

Ya that's what I have been doing so far :) But I thought that with gvfs-fuse thing, I could magically make it appear on Nautilus in a nice way. Well - we'll see. I kind of agree that it is hidden somewhere.

---

