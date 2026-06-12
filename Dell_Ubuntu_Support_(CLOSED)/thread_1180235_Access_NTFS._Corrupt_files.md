---
title: "Access NTFS. Corrupt files"
date: 2009-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ultimatebuster on 2009-06-06
Hi!
I have a inspiron 1525.
I was working on a website in Ubuntu with Kompozer on the shared data partition. I have a bran new hdd (10 days).

I partitioned my harddrive so it looks like this:
Win7(NTFS)|Shared Data(NTFS)|Ubuntu(ext3)

When i try to move a file from the website folder in the shared data partition, it told me that the file is corrupted and unreaderble. I ran chkdsk and found multiple errors at that location. The error is now fixed.

What happened?

Here is one of the chkdsk repair log:
> 25008: Start repair on 06/06/2009 at 15:07:18:958 26084: Deleting an index entry from index 0x1000000001e74 of file 0x6000000002da3. 27094: An index entry of index 0x1000000001e74 points to unused file 0x6000000002da3. 27293: File record 0x6000000002da3 maps to "\NOKCC\templates\index_style.css~". 25009: End repair on 06/06/2009 at 15:07:18:958 

BTW I use NTFS Configure Tool on ubuntu

---

### Post by ultimatebuster on 2009-06-07
bump!

---

