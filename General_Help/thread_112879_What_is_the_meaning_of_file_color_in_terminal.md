---
title: "What is the meaning of file color in terminal?"
date: 2006-01-05
forum: General Help
---

### Post by sbasak on 2006-01-05
Am I correct in saying that 

[COLOR="Blue"]blue [/COLOR]= directory
[COLOR="Lime"]green [/COLOR]= executable or recognized data file
[COLOR="Cyan"]sky blue[/COLOR] = linked file
yellow with black background = device

---

### Post by magnusbb on 2006-01-05
Yes, that's correct.

But if you don't like them, you're free to turn them off in .bashrc. The colors is a feature of the command "ls" called "dir-colors".

---

### Post by Galoot on 2006-01-05
[COLOR="Magenta"]magenta[/COLOR] = graphic image file

Are there others?

---

### Post by carlosqueso on 2006-01-05
[COLOR="Red"]Red[/COLOR]=archive file

---

### Post by kingsidy on 2006-01-05
i knew they meant something. i knew that directories were blue. that was it. thanks for pointing it out

---

### Post by Galoot on 2006-01-05
Aha!

```
man dir_colors
```shows these defaults and tells you how to change them.

```
NORMAL   0       Normal (non-filename) text
FILE     0       Regular file
DIR      32      Directory
LINK     36      Symbolic link
ORPHAN   undefined       Orphanned symbolic link
MISSING  undefined       Missing file
FIFO     31      Named pipe (FIFO)
SOCK     33      Socket
BLK      44;37   Block device
CHR      44;37   Character device
EXEC     35      Executable file
```

and

```
 0     to restore default color
 1     for brighter colors 
 4     for underlined text
 5     for flashing text
30     for black foreground
31     for red foreground
32     for green foreground
33     for yellow (or brown) foreground
34     for blue foreground
35     for purple foreground
36     for cyan foreground
37     for white (or gray) foreground
40     for black background
41     for red background
42     for green background
43     for yellow (or brown) background
44     for blue background
45     for purple background
46     for cyan background
47     for white (or gray) background
```

---

