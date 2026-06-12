---
title: "using the file browser"
date: 2006-07-20
forum: Desktop Environments
---

### Post by keheikev on 2006-07-20
[LIST=1]
[*]what happened to the file browser applet in dapper?
[*]I can get to the browser from the places/home or wherever menu
[/LIST]
[LIST]
[*]what is the purpose of a file system if nothing can be moved?
[/LIST]
However everything is locked down so I cant drag and drop 1 file from the desktop to a directory called /etc/java
whats the terminal command to move the file there?
Kiheikev
Aloha!

---

### Post by goobers on 2006-07-20
Its most likely because of privelages... you could try **sudo nautilus**

---

### Post by geco on 2006-07-20
> **keheikev said:**
> [LIST=1]
[/LIST]
[LIST]
[*]what is the purpose of a file system if nothing can be moved?
[/LIST]
However everything is locked down so I cant drag and drop 1 file from the desktop to a directory called /etc/java
whats the terminal command to move the file there?
Kiheikev
Aloha!

you need root privileges to move around directories that are not your home directory...
if you want a graphic tool, from terminal do:
```

sudo konqueror

```
or  "nautilus" if you use Gnome (I think nautilus it's the gnome file manager)
or just from terminal
```

sudo mv file_name /etc/java/

```

```

man mv

```
to see how mv works

---

### Post by keheikev on 2006-07-20
I looked in the man pages after I got the error cannot stat jre blah blah blah.bin
mv: cannot stat `jre-1_5_0_07-linux-i586': No such file or directory

do I have ta put a source argument to perform the move, the file is on the desktop. Why is it in the man pages that mv is title mv (rename)? Going to [www.linuxcommand.org](www.linuxcommand.org) to review the file system.
TIA
kiheikev
Aloha!

---

### Post by geco on 2006-07-20
sorry, what do you exactly want ti do?
install a package?
move a file?

---

### Post by keheikev on 2006-07-20
Yes I am going to install the sun java thingy. But I would like to move it to the recommended (by Sun) directory. So far not able to do the move. 
Kiheikev
Aloha
#-o

---

### Post by goobers on 2006-07-20
The easiest way is to type **sudo mv** into a terminal, then drag the file you want to move onto the terminal window (this will automatically enter the path  to the file) then enter the location you want to move it to

---

### Post by geco on 2006-07-20
ok let's state that you have to move the directory "dir_to_move" from your home directory /home/kiheikev to /etc/java using terminal
first of all you must check wether /etc/java exists
```

ls -ld /etc/java

```
if you have 
"ls: /etc/java: No such file or directory"
you must create it
```

sudo mkdir /etc/java

```
now you can make the move
```

sudo mv /home/kiheikev/dir_to_move /etc/java

```
you can check it with
```

ls -ld /etc/java/dir_to_move

```

if you want to move your dir_to_move directory and rename it java you have to skip the "mkdir" passage 

if mv says "mv: cannot stat `jre-1_5_0_07-linux-i586': No such file or directory" that means that you are trying to move a file/directory placed somwhere else (existing in local directory)

---

### Post by keheikev on 2006-07-20
Thank you  both that should give me something to think about and play with 
Kiheikev

---

### Post by goobers on 2006-07-20
no problem

---

### Post by keheikev on 2006-07-20
Well alrighty I dragged and dropped the file into the terminal. What I was missing was the destination of the file /etc/java. The dragging and dropping gave me the source 
mv source(path) /file_or directory /destination So now I have manually installed the binary. Now I have to create a sym-link between the new directory and the plugins. This is so i can view lake applets. 
Next step is enabling thunderbird to play midi files when I open mail with stationery.
Kiheikev
Aloha!

---

### Post by keheikev on 2006-07-20
So where is the default installation directory for mozilla-firefox
:-k 
Kiheikev
Aloha!

---

