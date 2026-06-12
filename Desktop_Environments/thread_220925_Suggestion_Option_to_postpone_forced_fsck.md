---
title: "Suggestion: Option to postpone forced fsck"
date: 2006-07-22
forum: Desktop Environments
---

### Post by scotty64 on 2006-07-22
I wonder if it would be possible to modify the boot process so that I can bypass the "maximum mount count reached -- check forced" when I press a certain key within - let's say 10 seconds. Another operating system does this and I find it very useful. It happened to me a couple of times that I was in a hurry or wanted to show something to somebody and fsck was forced. And it can take a while on a large hd!
With the modern journalling ext3 filesystem I do not see the need to check it exactly after 30 mounts...
Any ideas?

---

### Post by matthew on 2006-07-22
You can hit ctrl+c as it begins and it will stop and skip the check.

---

### Post by Anduu on 2006-07-22
IMHO this is a bad idea...it is done for a reason.A couple of times the forced check has found errors even tho I had no crashes and my PC was performing fine.

It is too easy to be "lazy' and just skip the ckeck every time.Over time this could cause some serious issues.

Just my 2 cents...

---

