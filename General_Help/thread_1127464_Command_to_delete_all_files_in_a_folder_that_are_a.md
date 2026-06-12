---
title: "Command to delete all files in a folder that are above a certain size required!"
date: 2009-04-16
forum: General Help
---

### Post by Rytron on 2009-04-16
Hi.
I need a command to delete all files in a folder that are above a certain size!

For example: I have a folder that has many files in it. I only want to keep files that are 5MB or less in size. There are many sub folders in the main folder.

Anyone?

---

### Post by codeseer on 2009-04-16
It'd probably be easier to just program it. This is going to get interesting.

Edit:

How about [this]("http://www.astahost.com/info.php/delete-files-by-size-recursively_t14747.html").

```

find /home/username/Desktop/sizetest/* -size +5M -type f -exec rm -f '{}' \;

```

Seems to work well.

---

### Post by Rytron on 2009-04-17
Thank you codeseer. Your code is excellent.

:popcorn:

---

