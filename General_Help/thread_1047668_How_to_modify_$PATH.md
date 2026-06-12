---
title: "How to modify $PATH"
date: 2009-01-22
forum: General Help
---

### Post by arsen13 on 2009-01-22
How can i modify directories that are in $PATH? I mean from file, I don't really want to do it every time that I log in.

Thanks

---

### Post by JMJ_coder on 2009-01-22
The file you need to modify is .bashrc .shrc (BASH) or .cshrc .tcshrc ((T)CSH).

There you can modify $PATH. For example, in my .cshrc, I have:

```
set path = ($PWD ~/bin /bin /sbin /usr/{bin,sbin,X11R6/bin,games} \
	    /usr/local/{,s}bin /usr/local/bin/java)
```

---

### Post by arsen13 on 2009-01-30
I don't have any path word in my .bashrc file and I don't have any of the other files.

---

### Post by taurus on 2009-01-31
If you want to add some directory to your path, open a terminal and edit your ~/.bashrc.

```
gedit ~/.bashrc
```
Add the following two lines to the end of it.

```
PATH=$PATH:/new_path:/another_new_path
export PATH
```
Save it.  Then either log out and back in or "source" it.

```
source ~/.bashrc
```

---

