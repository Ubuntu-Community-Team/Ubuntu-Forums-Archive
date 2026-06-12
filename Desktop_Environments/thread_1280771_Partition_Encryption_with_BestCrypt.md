---
title: "Partition Encryption with BestCrypt"
date: 2009-10-02
forum: Desktop Environments
---

### Post by Dezfor on 2009-10-02
Hello.
I wanna encrypt my user's partition and other folders, containing data(swap, temp folder)But i don't know how to implement this. Also, to encrypt system's partition.

And if it is possible to create another user, not encrypted, for routine needs because i live in Dorms and someone can ask my laptop, for example.

I read documentation on bctool and understood how to create containers. But after mounting - i can't add any information there through nautilus(ubuntu shows "/home/andrew/mount/1/new_folder»: Invalid or incomplete multibyte or wide character"). Only via using terminal's commands to copy/create folder or krusader. Although files and folders with russian names don't wanna be copied into container, even through terminal.
To create container i'm using such:
 ```
bctool new /home/andrew/docs.jbc -s 20M -a blowfish-448 -t ntfs -v
```
And when i try to open this containers in Windows - they are in ReadOnly mode
Help noob plzz :)

---

### Post by Dezfor on 2009-10-03
> **Dezfor said:**
> 
I read documentation on bctool and understood how to create containers. But after mounting - i can't add any information there through nautilus(ubuntu shows "/home/andrew/mount/1/new_folder»: Invalid or incomplete multibyte or wide character")
So, i found in the Net that containers with NTFS i should mount in other way. And saw advice to read man mount. I read it but cAn't understand nothing. How to mount such containers properly?

---

### Post by Dezfor on 2009-10-05
Help me pliz with encryption of home folder for user

---

