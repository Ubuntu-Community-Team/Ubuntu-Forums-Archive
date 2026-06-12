---
title: "Permissions of folder and subfolders/files?"
date: 2006-02-10
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2006-02-10
Hi, I was just curious as to how to change the permissions and ownership of a folder and all of it's contents (subfolders and files)?

---

### Post by cdhotfire on 2006-02-10
Folder or file
```

$ sudo chown USERNAME /folder/here/or/file

```

Subfolders and files
```

$ sudo chown USERNAME /folder/here/*

```
Keep putting /* depending on how deep you wanna go.

---

### Post by TheIdiotThatIsMe on 2006-02-10
Thanks a bunch! How do I change the permissions for all the files at once to allow the owner full read, write, and execute rights?

---

### Post by cdhotfire on 2006-02-10
```

$ sudo chmod 777 /folders/files

```

Thats for all everyone to have full read and write access you can try 700 for only yourself.

---

### Post by Sutekh on 2006-02-11
To do those command **recursively** ie change the folder and all folders beneath it, use the **-R** flag

```
sudo chown **-R** <username> /folders/files
```
Will change the ownership of /folders/files to the user <username>
```
sudo chmod **-R** 777 /folders/files
```
Will change the modes of access (permissions) of /folders/files to read/write/execute for everyone.

---

### Post by TheIdiotThatIsMe on 2006-02-11
Thanks a lot! I got everything working (my .kde folder had root only permissions so I was unable to get Amarok working properly). You guys rock :cool:

---

