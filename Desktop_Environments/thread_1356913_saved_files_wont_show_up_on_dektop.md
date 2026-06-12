---
title: "saved files wont show up on dektop"
date: 2009-12-16
forum: Desktop Environments
---

### Post by mikejaron on 2009-12-16
im using the newest ubuntu and when im online and download a file, (mainly .pdf) to my desktop it doesn't show up. even when i go into my filesystem and look under desktop its not there and its trying to load, but nothing ever shows up. but when i try to save something else to my desktop, like in office or an image, the files (the .pdf's that are not on the desktop) show up in the "save file" box and the saved file will show up on the desktop. Also i just started using chrome for my browser, it seemed to never do this before when i used firefox. but now when i do use firefox it does the same thing.

---

### Post by Yvan300 on 2009-12-16
You sure it did not save in downloads? That seems to be the default . Well if you're still getting those bugs then why not install chromium. Google chrome originated from this project. So they're basically the same.

---

### Post by Tek-E on 2009-12-16
Try using :

```

ls -al | grep name_of_file.jpg

```

To see if it is there.  You might just have to use ls -al.
If you find the file but with a dot before the name like
```

.filename.jpg

```

It means the file is being hidden when it is being saved.

I would check your download/save settings on your browser.

---

### Post by Tek-E on 2009-12-16
> **Yvan300 said:**
> You sure it did not save in downloads? That seems to be the default . Well if you're still getting those bugs then why not install chromium. Google chrome originated from this project. So they're basically the same.

Ha Ha Didn't even think of that.
+ 1

---

### Post by mikejaron on 2009-12-16
haha def did not save it to downloads, triple checked that

---

### Post by mikejaron on 2009-12-16
so i tried the code (ls -al | grep name_of_file.jpg) and it says that there is no such file or directory

---

### Post by mikejaron on 2009-12-16
thanks for all the help, it seems all my computer needs was a restart now everything is working fine

---

