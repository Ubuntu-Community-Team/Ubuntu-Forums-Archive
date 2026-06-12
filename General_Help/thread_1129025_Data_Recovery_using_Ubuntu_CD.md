---
title: "Data Recovery using Ubuntu CD"
date: 2009-04-18
forum: General Help
---

### Post by joscarjr55 on 2009-04-18
Long story short I have 2 hard disks for my laptop(HP)one I use as external(USB) and the other to boot. 

When I was using ubuntu it crashed and I couldnt get it to boot again so I changed to the other disk and installed on it Windows at the time I though it would be temporarily. 

Anyways time passed and I decided to get the data  back by booting from the Ubuntu Cd and then transfering it to the windows platform. 

Problem is that most of the files are locked by the password which I have but I dont know where I have to put it in to have full access to my old ubuntu hard disk. This doesnt let em copy open and stuff all of this data + the protection is not on all files but a number of them and it is basically random. As I never did this protection when I had control over the hard diska s a boot drive.


Do I make sense? Sorry but I am new to ubuntus and to forums

---

### Post by danwood76 on 2009-04-18
I am assuming you never encrypted the disk.

If that is the case you can run nautilus (the file manager) using root privilages from the command line by running:
```

sudo nautilus

```
This should then allow you to view all files on the drive no matter what permissions.

---

### Post by joscarjr55 on 2009-04-18
10x i will try

---

