---
title: "PLEASE HELP!!! almost out of hair!!!"
date: 2006-08-27
forum: Desktop Environments
---

### Post by shawnthecableguy on 2006-08-27
I have tried every possible way of creating a shortcut to my world of warcraft .exe in the fake c drive folder, but cant get it to run.

I keep getting this error:

Details: Failed to execute child process "/home/cableguy/.wine/drive_c/Program" (No such file or directory)

Any help is welcome!

Thanks](*,) ](*,) ](*,)

---

### Post by peabody on 2006-08-27
Sounds like you need to put quotes around the name

"path/to/program that includes/spaces"

You also need to run it using wine/cedega

---

### Post by shawnthecableguy on 2006-08-27
:KS 
THANKS!!

The quotes did the trick! : wine "/home/cableguy/.wine/drive_c/Program Files/World of Warcraft/WoW.exe"

the guide in the forum didnt say to use quotes.

Thanks again.:-D

---

### Post by peabody on 2006-08-27
> **shawnthecableguy said:**
> :KS 
THANKS!!

The quotes did the trick! : wine "/home/cableguy/.wine/drive_c/Program Files/World of Warcraft/WoW.exe"

the guide in the forum didnt say to use quotes.

Thanks again.:-D

You can omit quotes provided the file + path doesn't contain spaces.  If it does, you either have to quote with double or single quotes, or backslash escape each space.

---

