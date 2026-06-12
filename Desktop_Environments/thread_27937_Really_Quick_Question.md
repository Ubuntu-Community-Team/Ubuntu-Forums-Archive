---
title: "Really Quick Question"
date: 2005-04-18
forum: Desktop Environments
---

### Post by HeXetic on 2005-04-18
When using the cd command in the terminal it doesn't allow you to browse to that folder if there is a space in it. For example if I put 

```
cd My Music
``` 

It says there is no such directory. Is there a way around this other than naming the folder 1 word?

---

### Post by whittycat on 2005-04-18
You could try 
   cd My\ Music
or 
  cd 'My Music'
ie 'escape' the space

---

### Post by bassMonkey on 2005-04-18
cd My\ Music/

---

### Post by Stormy Eyes on 2005-04-18
Try **cd "My Music"** or **cd My\ Music** instead. Default Unix behavior is to treat the space as a separator; enclose the name in quotes or use an escape character to get around this.

---

### Post by bassMonkey on 2005-04-18
[QUOTE=whittycat]You could try 
   cd My\ Music
or 
  cd 'My Music'
ie 'escape' the space[/QUOTE]
 damn you!

---

### Post by Stormy Eyes on 2005-04-18
Jeez. Three simultaneous posts...

---

### Post by HeXetic on 2005-04-18
Thanks for that

---

### Post by timczer on 2005-04-18
You can add a underline between words in the file name when naming them: for exampe "file_name".  Or follow the howto that allows you to open a terminal in nautilus window [http://www.ubuntuforums.org/showthread.php?t=26668](http://www.ubuntuforums.org/showthread.php?t=26668).  I am sure there are better ways, but these work for me.

---

### Post by az on 2005-04-18
Use tab completion.

---

### Post by carlc on 2005-04-18
I use the path of least resistance- lower case folder names without spaces between words (even in XP).

---

