---
title: "How to change owners?"
date: 2009-12-07
forum: Desktop Environments
---

### Post by Ragde15 on 2009-12-07
I have a couple of files in my destop that are not mine however basically i was the one who got/downloaded it. I don't want to have to go to the other accound just to let mine have permission. I want to know if there is a way to change the owner of a file or document.

---

### Post by lloyd_b on 2009-12-08
> **Ragde15 said:**
> I have a couple of files in my destop that are not mine however basically i was the one who got/downloaded it. I don't want to have to go to the other accound just to let mine have permission. I want to know if there is a way to change the owner of a file or document.

Only the owner of a file or root can change the ownership on that file.  So either switch to that other user, or open a terminal window and "sudo chown {user} {filename}".

Lloyd B.

---

