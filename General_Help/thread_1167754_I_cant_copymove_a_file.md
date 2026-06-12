---
title: "I cant copy/move a file"
date: 2009-05-23
forum: General Help
---

### Post by Find on 2009-05-23
Hi

I had this rar archive which I extracted. Then when I want to move or copy the extracted file in the middle of copying/moving it gives me this error

Error while copying "file name"
Error reading from file: Input/output error

It happens even if I want to copy/move within the same folder, i.e. it copies the first lets say 200 MB and then it gives me the error above. It is the same whether I use Nautilus or Treminal

Thanks

---

### Post by KhurramM on 2009-05-23
whats the file type?

size of file(s)?

Is the space enough where u are copy/move file to?

try umount partition on which file resides. (CAUTION: Backup other data first)

do:

fsck /dev/sdb3 or what so ever.......

Hope this solves your problem.......):P

---

### Post by Find on 2009-05-23
Thanks for help.

It is a 700 MB avi movie, while I can copy the other files in the same folder with the same extension!
There is enough room in all the drives.
and it is on my system drive in
/opt/
and i think i can not umount that one, anyways, thanks again

---

