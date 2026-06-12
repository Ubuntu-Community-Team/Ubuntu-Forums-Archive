---
title: "open current folder from terminal"
date: 2012-05-15
forum: Desktop Environments
---

### Post by quangvinh on 2012-05-15
Hi all,
is there a way to open a new nautilus-window with the current folder  from terminal?
for example: i am in Terminal: quangvinh@ubuntu:~/Downloads$ 
and i want to put an command to open a window with Downloads folder.

I have Ubuntu 11.04 and standard graphic environment.
Thanks for help in advance.

---

### Post by hakermania on 2012-05-15
```

nautilus .

```
it is.

---

### Post by quangvinh on 2012-05-15
wow thanks,
i saw a friend just put "f" in his terminal and a the folder pop up. what does he use, do u know it?

---

### Post by matt_symes on 2012-05-15
Hi

> i saw a friend just put "f" in his terminal and a the folder pop up. what does he use, do u know it?

An alias ?

```
matthew@matthew-Aspire-7540 / % f
zsh: command not found: f
matthew@matthew-Aspire-7540 / % alias f=nautilus
matthew@matthew-Aspire-7540 / % f
matthew@matthew-Aspire-7540 / %
```

Kind regards

---

### Post by hakermania on 2012-05-15
> **quangvinh said:**
> wow thanks,
i saw a friend just put "f" in his terminal and a the folder pop up. what does he use, do u know it?

In order to do this, you have to edit the ~/.bashrc file
Go to your home folder using nautilus and give Ctrl+H, this will show the hidden files!
Navigate to .bashrc file and open it with Gedit.
Add this to the last line:
```
alias f='nautilus .'
```
and then restart your terminal (or give it 'source ~/.bashrc'). From now on, you will be able to open nautilus in the current (terminal's) folder by just giving 'f' :)

---

### Post by quangvinh on 2012-05-15
U guys are the best, thanks

---

