---
title: "mkdir directory"
date: 2009-01-18
forum: General Help
---

### Post by iEthan on 2009-01-18
This may sound stupid, but when I do the mkdir command in Terminal, where does it make the folder?

~iE

---

### Post by jflaker on 2009-01-18
If you just entered the terminal, you are in /home/YourUserID

If you mkdir, your folder is one level down from there....(PLACES>HOME)

You can then just cd to it.

---

### Post by Sorivenul on 2009-01-18
It depends.

If you are in your home directory and type:
```
mkdir Testfolder
```
The folder that is made would be /home/<username>/Testfolder.

If you just open a terminal and type:
```
sudo mkdir /opt/Testfolder
```
The folder that is made will be /opt/Testfolder.

In short, if you type a specific path, the folder will be in that path. If you just type a folder name, the folder will be created in the current directory.

Hope this helps!

---

### Post by 67GTA on 2009-01-18
If you don't specify where, it will be created in your /home folder. If you want to create a directory in the root "/" directory, you will have to specify where. Examples:

To create a directory in /etc (in the root directory) named nvidia, you would use ```
sudo mkdir /etc/nvidia
``` You have to use sudo to gain root powers to write to the root directory. 

To create the same directory in your home folder, you can just use ```
mkdir /nvidia
```

---

### Post by snova on 2009-01-18
At the command line, you are always "in" a directory (the "current working directory"). Commands are executed relative to this.

So "mkdir somefolder" would create it wherever you are currently located. When you first start the terminal, this is your home directory (/home/<username>, which can be abbreviated to ~/).

The 'cd' command moves around between directories.

> **Sorivenul said:**
> If you are in your home directory and type:
```
sudo mkdir Testfolder
```
The folder that is made would be /home/Testfolder.

If you were in /home, it would, but if you were in your home directory, it would be /home/<username>/Testfolder.

---

### Post by Sorivenul on 2009-01-18
> **snova said:**
> If you were in /home, it would, but if you were in your home directory, it would be /home/<username>/Testfolder.

True enough. :D An honest mistake, now corrected.

---

### Post by redonwhite on 2009-01-18
> **iEthan said:**
> This may sound stupid, but when I do the mkdir command in Terminal, where does it make the folder?

~iE

If you open the Terminal and type "mkdir test" it will create a directory named test in your home directory.

---

