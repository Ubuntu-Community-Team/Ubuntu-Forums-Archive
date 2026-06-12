---
title: "Memory allocation failed ?? Can't convert images."
date: 2009-01-10
forum: General Help
---

### Post by linuxisevolution on 2009-01-10
I was using the convert command like this: convert  /media/disk-1/november26/*.JPG /media/disk/images/more/*.bmp

convert: Memory allocation failed `/media/disk/images/more/*-0.bmp'.

That would convert and move about 1500 images to another partition. The problem is, as it does this, it uses 100% swap and only 400mb ram, so covert crashes. How do I prevent this? Is this too much for my 2.6ghz 4.5gb memory machine?


EDIT: Now, after doubling my swap size, here is the output.
convert: Memory allocation failed `/media/disk/images/more/*-49.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-50.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-51.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-52.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-53.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-54.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-55.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-56.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-57.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-58.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-59.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-60.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-61.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-62.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-63.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-64.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-65.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-66.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-67.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-68.bmp'.
convert: Memory allocation failed `/media/disk/images/more/*-96.bmp'.

---

