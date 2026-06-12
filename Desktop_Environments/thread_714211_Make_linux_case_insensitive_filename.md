---
title: "Make linux case insensitive filename"
date: 2008-03-03
forum: Desktop Environments
---

### Post by john_boys on 2008-03-03
hi, can any one tell me what code to modify in order to make Linux make case insensitive filename. i do not want the following file names to be created in the same folder:
ab.c
Ab.c
aB.c
AB.c
thanks

---

### Post by Matt Cadorette on 2008-03-06
Well, Unix and linux are case sensitive.  There isn't anything you can do about that, however 
 you can implement the case insensitivity yourself.  As an example:

ls|grep -i ab.c

This command will list all of the files because the -i makes grep insenative to case.  So there are ways to work around it, but it depends on what your doing.

---

### Post by HermanAB on 2008-03-06
Well, you can download the source code and modify everything, but don't expect to get much help from anyone for a project like that...

---

### Post by tubasoldier on 2008-03-06
The more you use *nix systems the more you realize how amazing case sensitivity really is. The fact of the matter is that 'a' is not the same character as 'A'. You can either use this to your advandage or your disadvantage. I personally make all my directories start with a capital letter and all my filenames start with lowercase. This way I can easily determine the type while in a terminal. It is difficult at first, but if you work with it your system can be more flexible and extensible.

---

### Post by boga on 2008-05-06
May be I'm a bit too late but just create a separate JFS partition for /home and format it with mkfs.jfs -O  This will create a case-insensitive JFS partition. It works fine for me as a /home though I'm unsure if it is going to work for /

---

### Post by sonny03 on 2008-06-21
Do one of these steps to make your linux case insensitive:

1) Use JFS (with option -O as your filesystem)
   *mkfs.jfs -O /dev/sda5*

2) Use ciopfs (Fuse Based filesystem). Visit this link for details [http://freshmeat.net/projects/ciopfs/?branch_id=74414&release_id=277441](http://freshmeat.net/projects/ciopfs/?branch_id=74414&release_id=277441)

---

