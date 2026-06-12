---
title: "help with clamav"
date: 2005-03-14
forum: Desktop Environments
---

### Post by ingvildr on 2005-03-14
i just installed clamav from the universe section and i ran a full scan "clamscan -r /" and it found one infected file. How do i find out what file it is and delete it???

---

### Post by kassetra on 2005-03-14
[QUOTE=ingvildr]i just installed clamav from the universe section and i ran a full scan "clamscan -r /" and it found one infected file. How do i find out what file it is and delete it???[/QUOTE]

Ok, clamscan stops at the first infected file... so what you want to do is run clamscan with the --stdout option so that it will give you a list of the files it is scanning, and when it finds the infected file, it will look something like this:
 ```
/tmp/test/error.hta: VBS.Inor.D FOUND
``` 

In this way, you'll be able to see the infected file and then just delete it.

---

