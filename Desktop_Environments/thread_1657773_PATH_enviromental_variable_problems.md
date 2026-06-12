---
title: "PATH enviromental variable problems"
date: 2011-01-01
forum: Desktop Environments
---

### Post by 71GA on 2011-01-01
Hello i have been trying to execute custom scripts in CLI and it works fine for some time and then it just stops. I added a path where scripts are by typing in a command:
```
export PATH=/home/ziga/codesourcery/bin:"${PATH}"
```I allso used same command in **/etc/bash.bashrc**. After a while my **/etc/bash.bashrc** is empty!? 

What is going on? Did i mess anything?

---

### Post by AlphaLexman on 2011-01-01
You should put the new $PATH in your ~/.bashrc
~/.bashrc is the last file invoked by the interactive shell.

---

### Post by 71GA on 2011-01-02
> **AlphaLexman said:**
> You should put the new $PATH in your ~/.bashrc
~/.bashrc is the last file invoked by the interactive shell.

Can you just tell me how to do this for this example path "/home/ziga/codesourcery/bin"... just soo that i ll do it right. 

TY

---

### Post by AlphaLexman on 2011-01-02
Just copy and paste into a terminal:
```
echo "PATH=${PATH}:/home/ziga/codesourcery/bin/" >> ~/.bashrc
```
Then,
```
source ~/.bashrc
```
will re-read the config file.

---

### Post by 71GA on 2011-01-08
Ty guys i am closing this thread now :) [SOLVED]

---

