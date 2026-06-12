---
title: "Alt+F2 for scripts in custom folder"
date: 2008-02-20
forum: Desktop Environments
---

### Post by rothy on 2008-02-20
Hi,

I'd like to run scripts in a folder ~/scripts with the run dialog box (Alt+F2). This folder is added to $PATH and the scripts are executable, but when typing a script command (eg start_app) in the run dialog, I get an error "file:////start_app" cannot be found.

How can I fix this?

gts,
rothy

---

### Post by p_quarles on 2008-02-20
In the terminal, edit your .bashrc file:
```
nano .bashrc
```
Add or uncomment the following:
```
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```
Now, move your customized scripts to ~/bin and you will be able to run them from the run dialogue. If you wish to leave them in ~/scripts, of course, you can just change the path in .bashrc.

---

### Post by rothy on 2008-02-20
Yup, this works. Thx !

---

