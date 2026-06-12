---
title: "Mounting  ubuntu drives in windows"
date: 2009-07-14
forum: Desktop Environments
---

### Post by pvpkiran on 2009-07-14
Hi ,
   I have installed Ubuntu inside windows.It is not a separate partition. 
In windows it has just created a folder .
  Installing like this(inside windows) do give me an option of dual boot and all other things. 

  Now i have a problem

Now i want to access the files i have created on ubuntu from windows. How do i mount it. since ubuntu is not installed as a separate partition instead it is installed inside windows, i doubt how to do it?

pls suggest 

Thank you

---

### Post by pvpkiran on 2009-07-23
Help

Thanx

---

### Post by pro003 on 2009-07-23
Are you able to see ANYTHING from Windows, i.e your files, etc..?

---

### Post by pvpkiran on 2009-07-23
No . In windows i hav only a folder . Inside that i have a folder called 
disks
which has a file named root.disk . It is around 28 GB(The space i allocated for ubuntu while installing).
And another file swap.disk which is around 1 GB.

Apart from these thr is nothing else except some files for GRUB etc


Thanx

---

### Post by pro003 on 2009-07-23
Can you explain how did you exactly install ubuntu, step by step if possible?

---

### Post by vanadium on 2009-07-23
Save your user documents that you create in Ubuntu on the Windows drive, not on the Ubuntu partition.

You could easily replace your "Documents" folder in Ubuntu by a symbolic link that points to a location on your Windows partition instead (e.g. your "My Documents" in Windows). That way, you would seamlesly be using hte same file storage both from within Windows and within Ubuntu.

You can create a symbolic link by pressing Ctrl+Shift then dragging the folder to another folder. In that other folder, a link to the folder you dragged will be created. A link in Ubuntu feels and behaves like a normal folder.

---

### Post by pvpkiran on 2009-08-06
That is all fine. But the problem is i dont hav much space in Windows drive. 
While installing ubuntu i allocated it 30 GB.

I have some space left in Ubuntu now. 
Now is it possible to deallocate from Ubuntu and allocate that space to windows drive.

Thank U

---

### Post by pro003 on 2009-08-06
> **pvpkiran said:**
> That is all fine. But the problem is i dont hav much space in Windows drive. 
While installing ubuntu i allocated it 30 GB.

I have some space left in Ubuntu now. 
Now is it possible to deallocate from Ubuntu and allocate that space to windows drive.

Thank U

am not quite sure, but you can give it a try with [lvresize]("linux.die.net/man/8/lvresize")

---

