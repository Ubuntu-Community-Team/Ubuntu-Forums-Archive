---
title: "history -c on startup"
date: 2005-08-10
forum: Desktop Environments
---

### Post by Fluffz on 2005-08-10
hi!

i will clean my bash history at start up ! how i can do ?
```
history -c
```

---

### Post by C38a7r1zvl on 2005-08-10
[http://sun.uni-regensburg.de/bash-1.14.2/html/features_22.html](http://sun.uni-regensburg.de/bash-1.14.2/html/features_22.html)

But I'm quite sure there is an option to do that automatically on logout?

---

### Post by Fluffz on 2005-08-11
hm isnt really helpful

---

### Post by bored2k on 2005-08-11
[QUOTE=Fluffz]hi!

i will clean my bash history at start up ! how i can do ?
```
history -c
```[/QUOTE]
 **a) **Upper panel > Preferences > Sessions > Startup Programs > Add > history -c

b) 1. ```
moi@chez:~$cat >> hscript.sh 
history -c
moi@chez:~$chmod +x hscript.sh
```
2. Upper panel > Preferences > Sessions > Startup Programs > Add > hscript.sh

Any of those should work should work

---

### Post by Fluffz on 2005-08-12
Hi!

doesnt work? i donno y ?

i did all u said, but after restart starting terminal the history still there !

 :roll:  u get it working on ur own ?

---

### Post by Gerie Langeveld on 2005-08-12
[QUOTE=Fluffz]Hi!

doesnt work? i donno y ?

i did all u said, but after restart starting terminal the history still there !

 :roll:  u get it working on ur own ?[/QUOTE]
 You could make the file: .bash_history not readable/writable with: chmod -rw .bash_history

Or you could add a line to your .bashrc which reads: unset HISTFILE
Then remove the file .bash_history

Both will prevent your history to be written to a file and therefore not visible the next time you log-on. (You first have to log-out of all shells to see the result.)

---

### Post by Fluffz on 2005-08-14
hi!

i cant find .bash_history . global search doesnt work
where i can find?

ty

---

### Post by dcraven on 2005-08-14
[QUOTE=Fluffz]hi!

i cant find .bash_history . global search doesnt work
where i can find?

ty[/QUOTE]

```

ls -a ~/ | grep bash
```

Cheers,
~djc

---

### Post by Gerie Langeveld on 2005-08-14
[QUOTE=Fluffz]hi!

i cant find .bash_history . global search doesnt work
where i can find?

ty[/QUOTE]

It's a hidden file; it starts with a "."

(The names could be different, I'm using a dutch desktop)

1) On the top panel select: Locations-->Find Files
2) A window will appear.
3) Enter .bash* in the top field.
4) Select "Show more options"
5) Change the "Available options" to "Show hidden and backup files"
6) Click the "Add" button next to it.
7) Click Search in the bottom right.
8) When .bash_history is found, right click on the file and choose "Move to Trashcan".
9) .bashrc will also be there. Right click it and choose "Open"
10) Add the line: unset HISTFILE
12) Save the file.
Now log off and back in again. The history should be empty, because it's not saved anymore.

Cheers,
Gerie.

---

### Post by dcraven on 2005-08-15
[QUOTE=Gerie Langeveld]
1) On the top panel select: Locations-->Find Files
2) A window will appear.
3) Enter .bash* in the top field.
4) Select "Show more options"
5) Change the "Available options" to "Show hidden and backup files"
6) Click the "Add" button next to it.
7) Click Search in the bottom right.
8) When .bash_history is found, right click on the file and choose "Move to Trashcan".
9) .bashrc will also be there. Right click it and choose "Open"
10) Add the line: unset HISTFILE
12) Save the file.
[/QUOTE]

Or type:
```
rm ~/.bash_history; echo "unset HISTFILE" >> ~/.bashrc
```
in the terminal.

~djc

---

