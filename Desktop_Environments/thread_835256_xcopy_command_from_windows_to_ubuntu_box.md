---
title: "xcopy command from windows to ubuntu box"
date: 2008-06-20
forum: Desktop Environments
---

### Post by babyrajT on 2008-06-20
HI All,

I am trying to copy folders(have files inside) from windows to samba server using xcopy command .The folder structure of the source is c:\www\1,2,3,4,...... this will increase each day and will change the files inside the folder on a daily or weekly basis.Now I mapped the samba share to the source windows server as /back (as z: drive)and   I am using xcopy /e /s /k /d /y c:\www z:\[www.It](www.It) is working fine .Becasue of a huge amount of files and folders, I am planning to copy only the updated and newly created folders and files only.Can any one help me to modify the existing command ?

Thanks in advance .

---

### Post by NilsE on 2008-06-20
This command will only copy new or newer existing files starting at the  high level folder and every folder and file under it.

xcopy c:\Windows\*.* d:\Ubuntu /e /y /d

Obviously replace the from and to locations. Run it in the dos prompt or a batch file.

---

### Post by babyrajT on 2008-06-20
I could't understand can you explain in detail?

Thanks

---

### Post by NilsE on 2008-06-20
> **babyrajT said:**
> I could't understand can you explain in detail?

Thanks
Not much to explain.  You said you already had a working command but was interested in one that would only copy new folder and files or ones that were changed.

So,

```
Replace this part of the command I provided with the address of the 
files you want to copy:
 
c:\Windows\*.* 

This format says copy everything within c:\Windows including folders and files. 
If you want to copy an entire drive it would be c:\*.*
```

```
Replace this part of the command I provided with the address of the 
place you want to copy to:

d:\Ubuntu
```
The switches at the end just say to do what you want.  All of the switch definitions are available in the help for xcopy so just do a help xcopy in a dos prompt and you can see what each does.

---

### Post by babyrajT on 2008-06-23
Hi 

First of all thank you for your time .The comand is working well.I want to know one more thing .This command will copy the changed files its ok .Is there any way to copy the changed files to a different location? so that I can transfer only the chnaged files to our local server.

Thanks
babyrajT

---

