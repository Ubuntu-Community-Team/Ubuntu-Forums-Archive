---
title: "Samsung 830 SSD in 11.10  - What speed should I see?"
date: 2012-02-25
forum: Desktop Environments
---

### Post by traverlaw on 2012-02-25
I installed a new Samsung 830 SSD (256 mb) 6Gb/s with a new install of 11.10 64-bit.  I'm using SATA-III

I get the following results after running sudo hdparm -t /dev/sda

Timing buffered disk reads: 718 MB in  3.00 seconds = 239.15 MB/sec

This seems to be somewhat less than Samsung advertises for the drive.

Am I missing something?

Here is my installation procedure:  [http://www.reddit.com/r/Ubuntu/comments/q414e/how_i_painlessly_migrated_from_a_toolarge/](http://www.reddit.com/r/Ubuntu/comments/q414e/how_i_painlessly_migrated_from_a_toolarge/)

Edit: Solved -  I replace the cable that I was using with the one that came with the SSD.  Now it is more than twice as fast:

 Timing buffered disk reads: 1478 MB in  3.00 seconds = 492.51 MB/sec

---

