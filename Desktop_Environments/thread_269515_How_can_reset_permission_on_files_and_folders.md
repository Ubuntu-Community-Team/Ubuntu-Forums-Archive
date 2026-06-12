---
title: "How can reset permission on files and folders ?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by tdog on 2006-10-01
Hello.
I needed to set permission on files and folders, and since i have no clue about console and comands, i made a mess out of my work.
I was wondring, dose anyone know how to Reset file and folder permission to original Ubuntu installation ??? 

I greatly apprecaite babystep on this matter .. 
thanks](*,)

---

### Post by kidders on 2006-10-01
What the original permissions were depends on the specific files. Where are they?

**chmod** is the command to use to tweak permissions. Use man chmod for more info.

---

### Post by armware on 2006-10-02
what would be a standard permission set for standard text files? 
i've tried all combinations of permissions and cannot open a folder, yet i can run gedit and use the open file dialog box to open the folder and pull the file i need. very annoying, and no permission set seems to solve it.

---

### Post by jazzgossen on 2006-10-02
For ordinary, non-executable files, good permissions could be rw-r----- (only user and group can read, and only user can write to the files).

Try "chmod u=rw *.txt" and then "chmod g=r *.txt" to set those permissions. (Or "chmod -R ..." if you need to do that recursively).

Oh, and if you can't open folders, the problem might be that you don't have "x" permission on them. The x on files means execute, but on directories, it means that you can open that directory. So also do "chmod a+x yourdirectory".

---

