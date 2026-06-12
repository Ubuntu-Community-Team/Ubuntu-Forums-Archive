---
title: "mdadm RAID5 array wont start"
date: 2010-07-27
forum: Desktop Environments
---

### Post by putters on 2010-07-27
hi,

after a failed upgrade from 9.10 to 10.04 I had to format my computer and do a clean install of 10.04, and now my mdadm raid5 array wont start.

my array is called "The Library", and i believe the space between "The" and "Library" is causing the command disk utility uses to start the array to fail.

The exact error is

An error occurred while performing an operation on "The Library" (RAID-5 Array): The operation failed  
  
Error  assembling array: mdadm exited with exit code 1: mdadm: unrecognised  word on ARRAY line: Library  
mdadm: unrecognised word on ARRAY line:  Library  
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error  
mdadm:  Not enough devices to start the array.  
  
im 99% sure the  problem is with the space, if it is, can I rename the array (and if so how?) or is something else?

cheers

---

### Post by jacekk015 on 2010-07-27
Try this to get UUID:
```
sudo mdadm -E /dev/sda1
```Instead of sda1 us your partition/disk that you had used with your array.

Then write down UUID and try to assemble by UUID instead of name:
```
sudo mdadm --assemble --uuid=xxxxxxxx ...
```

---

