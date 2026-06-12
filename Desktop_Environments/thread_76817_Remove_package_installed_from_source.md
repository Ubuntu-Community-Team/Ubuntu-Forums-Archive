---
title: "Remove package installed from source?"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Synt4x_3rr0r on 2005-10-15
As the topic says, how do i do this?
I've installed a package from source and now what should I do when i want to remove it?

Sorry if im in the wrong forum section, but i didn't know where to put it.

---

### Post by manicka on 2005-10-15
in the directory you compiled it in, type 

make clean

---

### Post by mcduck on 2005-10-15
I think it is done with command 'make remove' in the source directory. Doesn't make clean just clean the source directory?

---

### Post by Synt4x_3rr0r on 2005-10-15
After i did that, i could still start it. So i guess it didnt help :S

EDIT: mcduck: When i tried 'make remove' it said "no rule to create target 'remove'"

EDIT 2: I found the command by googling :D It was "make uninstall" :P

---

### Post by manicka on 2005-10-15
sorry, my bad, you are correct

---

