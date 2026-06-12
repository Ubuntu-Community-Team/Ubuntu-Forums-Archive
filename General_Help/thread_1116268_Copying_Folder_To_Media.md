---
title: "Copying Folder To Media"
date: 2009-04-04
forum: General Help
---

### Post by Miroku419 on 2009-04-04
Ok..  I want to copy a folder of music to my neice's psp...  the folder is located at /home/tommy/Desktop/Hannah and I want to copy it to /media/G1146092408/PSP/MUSIC  could you help with this?  I tried using the cp command but it wont work...  do I have to zip it then unzip when its on the psp or what?

when i try with the cp command it says "cp: omitting directory `/home/tommy/Desktop/Hannah'"

please help, thanks


EDIT: Also when I try to just move  it, it tells me that i dont have the permission to do it.  So afaik i need to use the cp w/ root or sudo.. but that wont work for me..

---

### Post by ukblacknight on 2009-04-04
> **Miroku419 said:**
> Ok..  I want to copy a folder of music to my neice's psp...  the folder is located at /home/tommy/Desktop/Hannah and I want to copy it to /media/G1146092408/PSP/MUSIC  could you help with this?  I tried using the cp command but it wont work...  do I have to zip it then unzip when its on the psp or what?

when i try with the cp command it says "cp: omitting directory `/home/tommy/Desktop/Hannah'"

please help, thanks


EDIT: Also when I try to just move  it, it tells me that i dont have the permission to do it.  So afaik i need to use the cp w/ root or sudo.. but that wont work for me..

You could try:

```
sudo cp /home/tommy/Desktop/Hannah/* /media/G1146092408/PSP/MUSIC
```

or alternatively, type:

```
sudo nautilus .
```

which will open nautilus as root, thus being able to move files where you want.

---

### Post by Miroku419 on 2009-04-04
> **ukblacknight said:**
> You could try:

```
sudo cp /home/tommy/Desktop/Hannah/* /media/G1146092408/PSP/MUSIC
```

or alternatively, type:

```
sudo nautilus .
```

which will open nautilus as root, thus being able to move files where you want.

Thanks... second one worked.

---

### Post by ajgreeny on 2009-04-04
Though in future please use ```
gksudo nautilus
``` or you might have problems.  See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more details of reasons for this.

---

### Post by ukblacknight on 2009-04-04
> **ajgreeny said:**
> Though in future please use ```
gksudo nautilus
``` or you might have problems.  See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more details of reasons for this.

My bad!  You learn something new every day!

---

