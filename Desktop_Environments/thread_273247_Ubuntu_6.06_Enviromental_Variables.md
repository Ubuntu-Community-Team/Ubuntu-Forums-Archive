---
title: "Ubuntu 6.06 Enviromental Variables"
date: 2006-10-07
forum: Desktop Environments
---

### Post by kwrxxx on 2006-10-07
I have a program that runs in TCL\TK that requires a enviromental variable to be set. If I run the program from the **_gnome-terminal_** command line the enviromental variable is recoginized. But if I run the program from the desktop the enviromental variable is not recoginized by the tcl\tk program. Even if I have set the desktop shortcut to ***run in the terminal*** in the program launcher the enviromental variable is not recoginized either. How do I fix this?

TIA

---

### Post by kwrxxx on 2006-10-07
I fixed my own problem by creating a **.gnomerc** file in my home directory and putting the variable there. 

```
export PATH="$PATH:$HOME/bin"
export tk92="/home/polk/bin/tk92"

```

---

