---
title: "[SOLVED] How can I find and fix broken links in my FS?"
date: 2008-12-20
forum: General Help
---

### Post by &amp;)ky#)^ on 2008-12-20
I recently noticed that Synaptic gave me a warning about a broken link while I was removing an old version of the kernel.  Unfortunately, it flashed by so fast I couldn't read exactly what file it was and the message wasn't logged in dpkg.log.  So, I used the following command to try to find all broken links in my system.
```
cd /
sudo find . -type l | (while read FN ; do test -e "$FN" || ls -ld "$FN"; done)
```
Unfortunately, it did give me pages of expected permissions errors when going through the /proc directory.  That made it tough to quickly weed out the errors.

Then I realized that even though a did find a couple of handfuls of broken links, would it be safe to delete the broken links or would that break more stuff.  I suppose it couldn't be worse than have broken links in the first place, but how did those links get there in the first place?

So, I'm looking for some advice.  What would be the best way to locate and remove all broken links from my filesystem?

---

### Post by dcstar on 2008-12-20
> **bluej774 said:**
> I recently noticed that Synaptic gave me a warning about a broken link while I was removing an old version of the kernel.  Unfortunately, it flashed by so fast I couldn't read exactly what file it was and the message wasn't logged in dpkg.log.
.........

Removing a kernel can cause that message because of the order that some things are deleted, but it is not important and nothing to worry about.

---

