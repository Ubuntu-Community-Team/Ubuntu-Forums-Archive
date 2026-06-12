---
title: "Renaming Multipal Folders"
date: 2011-06-08
forum: Desktop Environments
---

### Post by parag.nehete on 2011-06-08
Hi Friends,
I have around 150+ folders in one directory. All contains some pdf  files. Now i want to give some prefix no. to folder only not the files  inside. How can i give the prefix to all my folders?
 
Eg : Suppose i want no. 8562 then i want it like as follows

                            OLD FOLDER                                     NEW FOLDER
                                            ABC/                                                                 8562-ABC/
                     AABC/                                                            8562-AABC/
                     XYZ/                                         8562-XYZ/

I can't install any application as want to do it on server. Script will help me a lot.

Thank You,
Parag Nehete.

---

### Post by jwcalla on 2011-06-08
how about:

```
rename 's//8562-/' */
```

try it on some temp dirs first to make sure... ;)

---

### Post by parag.nehete on 2011-06-08
Hey thank you so much.......
It makes my work too easy....
thank u soo much

---

