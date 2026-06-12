---
title: "attachment size"
date: 2010-05-01
forum: Forum Feedback &amp; Help
---

### Post by chucky chuckaluck on 2010-05-01
any chance the size of allowed attachments could be made larger in order to accomodate 1280x800 screenshots?

---

### Post by matthew on 2010-05-01
I'm afraid not. We had to institute the (somewhat severe, I admit) limits due to server capacity limitations. Until/unless we are able to upgrade, and there is nothing planned in the immediate future, I suggest that you use a third party hosting site and link to the images. It is an imperfect solution for a reasonable request that I would like to approve, but we just can't as things are. Sorry. :(

---

### Post by chucky chuckaluck on 2010-05-01
i was using omploader.org, but they appear to have thrown a shoe. thanks, i figured it was something like that.

---

### Post by lavinog on 2010-05-02
> **matthew said:**
> I'm afraid not. We had to institute the (somewhat severe, I admit) limits due to server capacity limitations. Until/unless we are able to upgrade, and there is nothing planned in the immediate future, I suggest that you use a third party hosting site and link to the images. It is an imperfect solution for a reasonable request that I would like to approve, but we just can't as things are. Sorry. :(

What doesn't make sense is that you implemented a resolution limit and not a file size limit.
Currently a 976k bmp is permitted as long as the resolution is under 1024x 768:
```

test.bmp: PC bitmap, Windows 3.x format, 1024 x 768 x 24
-rw-r--r-- 1 greg greg 2.3M 2010-05-02 11:33 test.bmp

```
And I can have a desktop screenshot take up much less:
```

Screenshot-1_50.jpg: JPEG image data, JFIF standard 1.01
Screenshot-1.jpg:    JPEG image data, JFIF standard 1.01
Screenshot-1.png:    PNG image, 1280 x 800, 8-bit/color RGB, non-interlaced
-rw-r--r-- 1 greg greg  95K 2010-05-02 11:38 Screenshot-1_50.jpg
-rw-r--r-- 1 greg greg 151K 2010-05-02 11:37 Screenshot-1.jpg
-rw-r--r-- 1 greg greg 476K 2010-05-02 11:36 Screenshot-1.png

```

Of course bmp files should be rare, but my point is that even jpg files can take up more space than an optimized png file.

I am not recommending that full size screenshots be allowed...I am just saying it would make more sense to expand the resolution limit and reduce the file size to something like 80k.
Many of my attachments are no larger than 20k, and usually are less than 10k.

What if the forum had some way to purge files older than X days and larger than some size?  Maybe users can get a quota for their total attachments.

---

