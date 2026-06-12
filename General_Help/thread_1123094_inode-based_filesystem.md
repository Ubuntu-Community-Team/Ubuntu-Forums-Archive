---
title: "inode-based filesystem"
date: 2009-04-11
forum: General Help
---

### Post by amarkitanis on 2009-04-11
Ok I have a question about creating files on an inode-based file system.

If you want to create a file of 1025 bytes long....

Assumptions:
and you know that it takes 128 bytes to create a new inode,
and in the inode itself, you can store 64bytes of **data**, you have another 6 direct pointers to data blocks, one indirect pointer and one double indirect poiter. the rest of the bytes is simply accounting information that we're not interested for this question I'm posing.


Assume that disk addresses are 4bytes longs and disk blocks 1KB.


so my question is, how much space is 1025bytes of data ACTUALLY taking? (including overhead)

---------

my guess is, that it would require an inode for sure, so 128 bytes for that

so if the inode can store 64bytes in it directly, then you have 1025-64 bytes = 961 left to store

where I am puzzled is here....

does that get stored in an direct block and so we're wasting 1024-961 = 63 bits?

and so overhead is = (1024 + 128 - 1025) 

is that right?

Thanks for your time.

P.S if you think this is my homework, it's not. it's just an exam based question which i'm trying to solve in order to prepare for my exam, and all im asking is whether im correct or going wrong.

---

