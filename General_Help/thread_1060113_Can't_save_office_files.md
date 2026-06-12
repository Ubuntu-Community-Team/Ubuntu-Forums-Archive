---
title: "Can't save office files"
date: 2009-02-04
forum: General Help
---

### Post by bba1973 on 2009-02-04
Hello,

I was typing up my homework today in Open Office, but it woudln't save. Gave me some kind of error. Tried saving in different formats and such, but it still wouldn't save. Downloaded and installed AbiWord, but it does the same thing. I'd really like to be able to save my homework, so please help. Edited the permissions to create and delete files, but no help. Thanks for reading.

---

### Post by cariboo on 2009-02-04
You're a little bit short on information, where are you trying to save your files to. I'll assume you're trying to save to a flash drive.

Flash drives are usually mounted in /media/disk. To be able to save to the flash drive you need to change the permissions to world readable. To do this open a Applications-->Accessories-->Terminal and type:

```
sudo chmod -R 777 /media/disk
```

This will change the permissions on the flash drive to world readable allowing you to save your files to the drive.

Jim

---

### Post by bba1973 on 2009-02-04
I'm trying to save them in my Documents folder on my hard drive. Just got wine and office 2007, and it's saving things fine. Only problem with that so far is I don't see times new roman font, and I need that for school.

For some reason, it's working now. I just installed a bunch of updates, so that might be why. Problem resolved. Thanks for the reply Jim. Now I just need my printer to work.

---

