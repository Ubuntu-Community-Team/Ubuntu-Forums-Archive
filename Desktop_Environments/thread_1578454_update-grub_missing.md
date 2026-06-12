---
title: "update-grub missing?"
date: 2010-09-20
forum: Desktop Environments
---

### Post by stbub on 2010-09-20
The software update failed when the kernel update failed:

"Could not find postrm hook script [update-grub]."

Looking more closely, I can't find update-grub anywhere on disk, even though /etc/kernel-img.conf wants this.  I ran:

sudo find / -name update-grub 2>/dev/null

And it's missing.

I'm using 10.04, 64bit, with an nvidia adapter.

---

