---
title: "[SOLVED] Some files won't transfer to external HD?"
date: 2009-01-02
forum: General Help
---

### Post by Lokine on 2009-01-02
I'm backing up all of my music on my currently unused external hard drive. I transferred almost all of the files over with no problem, but a couple folders and a couple single files didn't make the transfer. I didn't run out of room by any means and the files that got left behind can be moved and copied on my main hard drive with no problem. Any ideas what might be going on here and how to solve it?

---

### Post by Tim Sharitt on 2009-01-02
Did you get any errors for the files that failed to copy?

---

### Post by Lokine on 2009-01-02
It's giving me an invalid parameters error, same one for each file that won't move.

---

### Post by dcstar on 2009-01-02
> **Lokine said:**
> I'm backing up all of my music on my currently unused external hard drive. I transferred almost all of the files over with no problem, but a couple folders and a couple single files didn't make the transfer. I didn't run out of room by any means and the files that got left behind can be moved and copied on my main hard drive with no problem. Any ideas what might be going on here and how to solve it?

Your external drive is probably formatted as FAT32 so it cannot accept certain characters as names that are allowed on Linux filesystems.

---

### Post by Lokine on 2009-01-02
> **dcstar said:**
> Your external drive is probably formatted as FAT32 so it cannot accept certain characters as names that are allowed on Linux filesystems.

You're exactly right. I just realized that each file that wouldn't transfer has a question mark in the filename. Thanks!

---

### Post by dcstar on 2009-01-02
> **Lokine said:**
> You're exactly right. I just realized that each file that wouldn't transfer has a question mark in the filename. Thanks!

You're welcome, and well done on marking the thread as closed!

---

