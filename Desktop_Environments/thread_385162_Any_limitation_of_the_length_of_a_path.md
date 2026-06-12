---
title: "Any limitation of the length of a path?"
date: 2007-03-15
forum: Desktop Environments
---

### Post by balaoko on 2007-03-15
I have access to a windows network drive through samba. When I run a matlab program to read a file in that drive, an error occurs: "File not found". The length of the path plus the file name is 125. Other files in that drive but with shorter path can be read.

Does anybody know whether there is a limitation in the path length in linux, or in matlab? How can I config something so that the file can be read from the network drive?

Thanks a lot.

---

### Post by ComplexNumber on 2007-03-15
> **balaoko said:**
> I have access to a windows network drive through samba. When I run a matlab program to read a file in that drive, an error occurs: "File not found". The length of the path plus the file name is 125. Other files in that drive but with shorter path can be read.

Does anybody know whether there is a limitation in the path length in linux, or in matlab? How can I config something so that the file can be read from the network drive?

Thanks a lot.
i don't think there is much limitation on path length. but, linux isn't all that brilliant at handling paths when they have spaces in them. enclose paths with quotes and it should be ok.

---

### Post by balaoko on 2007-03-15
Thanks, ComplexNumber.

I don't have spaces in the path. After the long name of a folder was changed a little, the path length was reduced to 122, and then the file can be read. I may have to be very careful when creating new folders.

---

