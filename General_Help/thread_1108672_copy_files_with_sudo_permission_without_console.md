---
title: "copy files with sudo permission without console"
date: 2009-03-27
forum: General Help
---

### Post by superalanliu on 2009-03-27
I want to copy files to a protected folder. I am currently doing this using the console and sudo. Is there an easy gui drag and drop method where it just prompts me for the password? The same applies to editting said files, is there a easy way to open a program with sudo? Besides gedit blah, is there a way where I just click and enter password?

Thanks,
Alan

---

### Post by Anxious Nut on 2009-03-27
try typing in the terminal
```
sudo nautilus
```
this will open nautilus as a root, you can do whatever you want, but be careful with important files

---

### Post by bodhi.zazen on 2009-03-28
You really should use gksu for graphical apps :

```
gksu nautilus
```

---

### Post by ryanhaigh on 2009-03-28
The easiest way is using the "Open as administrator option" which you get after installing this: [apt://nautilus-gksu]("apt://nautilus-gksu")

---

### Post by superalanliu on 2009-03-29
Whats the different between sudo and gksu? They both work though, so thanks!

---

### Post by ryanhaigh on 2009-03-29
[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

### Post by bodhi.zazen on 2009-03-29
> **superalanliu said:**
> Whats the different between sudo and gksu? They both work though, so thanks!

Yes both give root access. gksu is for graphical applications, sudo is for non-graphical applications.

gksu give access to X (in a safer way) as well as root.

See [RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

