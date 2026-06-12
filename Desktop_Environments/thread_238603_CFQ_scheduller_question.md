---
title: "CFQ scheduller question"
date: 2006-08-17
forum: Desktop Environments
---

### Post by veli on 2006-08-17
I changed the IO scheduller in both GRUB and by appending a file in RC6 I think, and after that I checked it out and this is the output:

noop [anticipatory] deadline cfq
noop anticipatory deadline [cfq]
noop anticipatory deadline [cfq]

I'm just wondering what those three lines mean, and why in the first line the scheduller is still the default.

Thanks a lot.

---

