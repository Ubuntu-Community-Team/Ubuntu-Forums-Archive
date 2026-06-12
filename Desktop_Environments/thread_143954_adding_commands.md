---
title: "adding commands"
date: 2006-03-13
forum: Desktop Environments
---

### Post by drguitarum2005 on 2006-03-13
Simple question...how do you create commands that ubuntu will recognize? by that I mean, say I install something in a certain path, to execute that thing, i have to type the whole path in the alt+F2 run window. how do i make it so just tpying the program name will run it? thanks

---

### Post by aysiu on 2006-03-13
You shouldn't have to type the whole path if it's in /usr
For example, if I put restore_mozilla_icons in /usr/local/bin, I can run the command *sudo restore_mozilla_icons*. I don't have to run *sudo /usr/local/bin/restore_mozilla_icons*.

---

### Post by art on 2006-03-13
You can define an alias in .bashrc in your home directory. There are some examples in this file($HOME/.bashrc) already to get you started.

---

### Post by taurus on 2006-03-13
If you install programs in somewhere else besides /bin, /usr/bin, or /usr/local/bin, then you need to add it to your PATH in ~/.bashrc.
```

gedit ~/.bashrc

```
If you don't see a line that starts with PATH, then add the following two lines to it, ~/.bashrc...
```

PATH=$PATH:/path_to_where_you_install_your_programs
export PATH

```
Save it and at the prompt, run
```

source ~/.bashrc

```
Now, just type in the name of the program and it will run, withouth specifying the whole path...

---

### Post by Jawbreaker4Fs on 2006-03-13
could this problem be solved by writing a shell script to launch the application and putting it in one of those directories?

---

### Post by taurus on 2006-03-13
Yes, it could.

---

