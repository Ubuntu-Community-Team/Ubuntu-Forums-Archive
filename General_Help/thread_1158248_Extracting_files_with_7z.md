---
title: "Extracting files with 7z"
date: 2009-05-13
forum: General Help
---

### Post by blckpythn on 2009-05-13
After installing 7z
I used the terminal 

7z e <filepath>

It did say it extracted successfully.
But I don't know where it extracted it to.
Anyone know if there is a default directory or if I have to set one or what?

---

### Post by alphaniner on 2009-05-13
I'm fair sure it extracts to the directory you were in when you ran the command.  If not there, then maybe the directory where the archive you extracted was located.

---

### Post by blckpythn on 2009-05-13
hehe well... um.. i found it

it went to my /home/matthew directory

loose files everywhere... ooops... yeah so how do i change the directory

---

### Post by chili555 on 2009-05-13
> so how do i change the directoryIn a terminal:```
mkdir anynameyoulike
mv loosefile#1 anynameyoulike
mv loosefile#2 anynameyoulike
```This is a pet peeve of mine; files that extract loose, rather than to a directory. I usually create a directory:```
mkdir myproject
```Then move the file you want to extract into it:```
mv project.zip myproject
```Change directories to the new directory and extract the file:```
cd myproject
7z e project.zip
```Then all the loose ends are contained.

---

### Post by linux_holic on 2009-05-13
hi,.

To *extract*: *tar* xvjf package.*tar*.bz

i hope it will help you...;)

---

### Post by blckpythn on 2009-05-13
well the .rar file is on my desktop but it automatically chose to put it in my home/matthew folder
how do i change the folder it extracts TO?

and another question

when im playing games fullscreen, something randomly steals my cursor for a moment and then my game is in like a window with my panels on the top and bottom showing, what causes that?

---

### Post by logos34 on 2009-05-13
> **blckpythn said:**
> well the .rar file is on my desktop but it automatically chose to put it in my home/matthew folder
how do i change the folder it extracts TO?


for .7z files:

> 7z e -o/path/to/outputfolder archive.7z

but as for rar, the man page just shows:

 > e             Extract files to current directory 

so wherever you run the command is where they should end up

---

