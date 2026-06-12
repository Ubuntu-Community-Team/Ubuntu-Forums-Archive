---
title: "I just need to navigate to the desktop in the terminal..."
date: 2009-02-16
forum: General Help
---

### Post by Nerv68 on 2009-02-16
Im typing in 'cd \home' and 'cd home', and it says there is no such directory. Please help... and forgive me, Im a nebie to linux.

---

### Post by scouser73 on 2009-02-16
Paste this code into terminal **> cd Desktop**

---

### Post by Nerv68 on 2009-02-16
ooooooooooh ok thanks. I didnt know it was case sensitive. Why cant I go to the home folder though?

---

### Post by ubersolid on 2009-02-16
> **Nerv68 said:**
> ooooooooooh ok thanks. I didnt know it was case sensitive. Why cant I go to the home folder though?

You are in your home folder when you start the terminal.
```
/home/*yourusername*
```
if you want to go one level up, you can either type ```
cd /home
```
or just ```
cd ..
```
To list what's in a folder, type ```
ls
```
And going back to ```
/home/*yourusername*
```
just type in ```
cd
```

---

### Post by mb_webguy on 2009-02-16
The tilda ("~") is also shorthand for your home directory.  So if you're off somewhere else and you want to go straight to a folder in your home directory, you can use "cd ~/wherever", which would be the same as "cd /home/you/wherever".  If you just want to go straight to your home directory, you can just use "cd" by itself.

You can see what directory you're currently in with the command "pwd", which stands for "print working directory".

As ubersolid said, the "ls" command will show you the files and directories in the current directory, but only the visible ones.  Files and directories which have a name beginning with a dot (".") are hidden.  You can see them by using the "-a" option of "ls" (i.e. "ls -a" to list all files and directories in the current directory).

---

### Post by sofasurfer on 2009-02-16
In you're question you typed "cd \home". It should be "cd /home".

---

