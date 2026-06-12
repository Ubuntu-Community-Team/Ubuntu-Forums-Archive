---
title: "How TO loCk the Folder"
date: 2009-04-06
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-06
****how to locker folder using software... any one know means reply me... i need the software..

---

### Post by ryanhaigh on 2009-04-06
I remember reading a couple of threads in the past about locking a folder. The easiest way is to change the permissions of the folder so that no one can read/write/execute:
```
chmod a-rwx ~/lockedfolder
```
You will need to grant permissions again to do anything with the folder.
```
chmod u+rwx ~/lockedfolder
```
That will give the user read/wrote/execute permissions.

---

### Post by ShaunG on 2009-04-06
Instead of locking a folder with software you could set the permissions on it to be read, write and execute only by root. Or you could encrypt it. Ubuntu has a default encryption thingy built in. Right click on the folder and choose encrypt.

---

### Post by suresh_vandiyur on 2009-04-06
> **ryanhaigh said:**
> I remember reading a couple of threads in the past about locking a folder. The easiest way is to change the permissions of the folder so that no one can read/write/execute:
```
chmod a-rwx ~/lockedfolder
```
You will need to grant permissions again to do anything with the folder.
```
chmod u+rwx ~/lockedfolder
```
That will give the user read/wrote/execute permissions.
thank u so much

---

### Post by suresh_vandiyur on 2009-04-06
> **ShaunG said:**
> Instead of locking a folder with software you could set the permissions on it to be read, write and execute only by root. Or you could encrypt it. Ubuntu has a default encryption thingy built in. Right click on the folder and choose encrypt.
 i had right click folder encrypt windows was opened.. then whan can i do???... reply me..

---

