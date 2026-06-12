---
title: "Does Grub add post-MBR code to first track?"
date: 2012-05-07
forum: Desktop Environments
---

### Post by andrekp on 2012-05-07
I have a dual boot (XP, Ubuntu, various other Linux) system.

I am using Ubuntu to boot the system.  I was using Grub2, but more recently, I started using Burg.

I recently noticed that the first 50 sectors of my main drive have code in them.  The first sector is obviously the MBR, but I would have expected the rest to be zero (at least for the most part).

Does Grub and/or Burg load code into that post-MBR section of the first track?

I'm wondering if this code might be indicative of something bad having installed itself there.  

Thanks

---

