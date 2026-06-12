---
title: "Write Speed into a big file (in Gb's)"
date: 2009-01-20
forum: General Help
---

### Post by anilgurwara on 2009-01-20
If a file size increases in Linux/UNIX to say in GB's then will there be a decrease in write speed.
I mean will it take more time to write to a large file then to a small one

Thanks in advance

---

### Post by mcduck on 2009-01-20
> **anilgurwara said:**
> If a file size increases in Linux/UNIX to say in GB's then will there be a decrease in write speed.
I mean will it take more time to write to a large file then to a small one

Thanks in advance

Depends on the file system you are using, not the OS itself.

Ext3 (the default in Ubuntu) is not specially good in anything, but at the same time not bad at anything. Bit of jack-of-all-trades.

ReiserFS is great with loads of small files but worse with very large files

JFS is good for large files but worse fr loads of small files.

I'd say the biggest difference in write speed with large files comes from the fact that your hard drives internal cache isn't able to store all data, meaning that the write speed is defined by the disk itself+file system instead of disk bus+file system.

(and yes, of course writing large file takes longer than small file, you have more data to write. But I assume you didn't mean this question literally but instead asked if there's difference in the write speed when comparing small files with large files ;))

edit: read this: [http://linuxgazette.net/122/TWDT.html#piszcz]("http://linuxgazette.net/122/TWDT.html#piszcz")

---

### Post by anilgurwara on 2009-01-20
Thanks a lot..

---

