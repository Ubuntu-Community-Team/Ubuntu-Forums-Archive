---
title: "How can I fix the color indicators in bash"
date: 2009-07-03
forum: Desktop Environments
---

### Post by Jem Masters on 2009-07-03
I have a problem with the bash, It doesn't show the color indicators for folders or executables in the terminal. Does anyone got the same problem? How can I fix this?

Thx, in advance.):P

---

### Post by Boondoklife on 2009-07-03
Try  
```
ls --color=auto
```
If that works then check in .bashrc and look for a line similar to alias ls='ls --color=auto' and uncomment it or add it if need be.

---

### Post by Jem Masters on 2009-07-10
The ls --color=auto work but I add it to bash.bashrc like you said and nothing, I just wrote down "ls= 'ls --color=auto' and nothing. Thank you anyway.

---

### Post by Boondoklife on 2009-07-10
ok you said bash.bashrc, was that the name of the file if so then you have the wrong name, you also need to login in then out to get it to take effect on the terminal.

---

### Post by Jem Masters on 2009-08-15
I don't seem to find the .bashrc  I have bash.bashrc.

---

### Post by Jem Masters on 2009-08-15
Forget what I said before, I found the .bashrc, but the instruction that you told me to uncoment is already uncomented and still don't work.

---

