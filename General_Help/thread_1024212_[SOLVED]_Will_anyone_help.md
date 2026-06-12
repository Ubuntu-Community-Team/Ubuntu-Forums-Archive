---
title: "[SOLVED] Will anyone help"
date: 2008-12-28
forum: General Help
---

### Post by borisagrees on 2008-12-28
Code??
I dont mean to be a pain but can you explain the code in this a little better. I am familiar with windows


Quote:
o use a .run or .bin file use the following in console:

Code:
chmod +x file.run
./file.run
As for drivers I have found using EnvyNG is the best/easiest way to install them.


~Jeff

---

### Post by SuperSonic4 on 2008-12-28
It means opening a terminal (Applications -> Accessories -> Terminal) and copy and pasting ```
chmod +x file.run
``` then
```
./file.run
``` where file is the name of the file, like nvidia-pkg-177.run or something. This will make it executable and then run it.

EnvyNG is a way of installing it without the command line. Go to Synaptic and search for EasyNG, when downloaded open and run

---

### Post by howefield on 2008-12-28
Beaten to it, although terminal is usually found in Applications > Accessories > Terminal. :)

---

### Post by borisagrees on 2008-12-28
> **SuperSonic4 said:**
> It means opening a terminal (system -> Administration -> Terminal) and copy and pasting ```
chmod +x file.run
``` then
```
./file.run
``` where file is the name of the file, like nvidia-pkg-177.run or something. This will make it executable and then run it.

EnvyNG is a way of installing it without the command line. Go to Synaptic and search for EasyNG, when downloaded open and run


do i have to put any directories like i do in windows?

```
./file.run
```

for example in windows (if i were using CMD) i would have to type

```
 start C:\documents and setting\TOSHIBA\file.exe 
```

[edit] oh and do i have to put it somewhere e.g desktop[/edit]

---

### Post by howefield on 2008-12-28
> **borisagrees said:**
> do i have to put any directories like i do in windows?

Yes, although you might need to navigate to the folder where you have your file. Remember linux is case sensitive, so Desktop is different to desktop

---

### Post by borisagrees on 2008-12-28
> **howefield said:**
> No, although you might need to navigate to the folder where you have your file.

how is that done in terminal?

---

### Post by SuperSonic4 on 2008-12-28
```
cd <folder you downloaded it to>
```
If this is the desktop:

```
cd ~/Desktop
```

---

### Post by borisagrees on 2008-12-28
> **SuperSonic4 said:**
> ```
cd <folder you downloaded it to>
```
If this is the desktop:

```
cd ~/Desktop
```

 well ill be a command the same as windows thanks for your help

---

### Post by howefield on 2008-12-28
pwd to tell you where you are and cd to change directory, ls will list the files in the directory.

If you have downloaded the file to your desktop, opening terminal and typing 

```
cd Desktop
``` 

should take you there, and ls will confirm by listing the files of the folder that you are in.

---

### Post by BatsotO on 2008-12-28
Since you seem familiar with cmd this might help [http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html](http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html)

---

