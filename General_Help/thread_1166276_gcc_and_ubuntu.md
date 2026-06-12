---
title: "gcc and ubuntu"
date: 2009-05-21
forum: General Help
---

### Post by darind on 2009-05-21
I'm using Ubuntu 8.10 on a System76 laptop.  When I write a little C program and type "gcc trial.c", i get permission denied.  Just out of curiosity, I tried "sudo gcc trial.c" and get sudo: gcc: command not found

How can I compile C programs?

Thanks for any assistance.

---

### Post by geirha on 2009-05-21
Can you post the exact message you get when you do "gcc trial.c" (without sudo)?

---

### Post by mcduck on 2009-05-21
> **darind said:**
> I'm using Ubuntu 8.10 on a System76 laptop.  When I write a little C program and type "gcc trial.c", i get permission denied.  Just out of curiosity, I tried "sudo gcc trial.c" and get sudo: gcc: command not found

How can I compile C programs?

Thanks for any assistance.

have you installed the compiler & other stuff needed for compiling programs? They are not included in default Ubuntu setup as most people will never need them.

If you haven't done that, run this command to install everything required:
```
sudo apt-get install build-essential
```

---

### Post by darind on 2009-05-21
I get

bash: /usr/bin/gcc: Permission denied

when I am just using Terminal and I get 

/bin/sh: gcc: Permission denied
Process terminated with status 126 (0 minutes, 0 seconds)
0 errors, 0 warnings

when I try to compile in Code:Blocks IDE

---

### Post by darind on 2009-05-21
> **mcduck said:**
> have you installed the compiler & other stuff needed for compiling programs? They are not included in default Ubuntu setup as most people will never need them.

If you haven't done that, run this command to install everything required:
```
sudo apt-get install build-essential
```



Yeah, I have already done that.  Thank you for verifying though.

---

### Post by geirha on 2009-05-21
That means /usr/bin/gcc doesn't have the execute permission set for some reason. Try reinstalling the gcc package
```
sudo aptitude reinstall gcc gcc-4.2
```

---

### Post by darind on 2009-05-21
> **geirha said:**
> That means /usr/bin/gcc doesn't have the execute permission set for some reason. Try reinstalling the gcc package
```
sudo aptitude reinstall gcc gcc-4.2
```


geirha, when you're a genius, you are simply a genius.  Thank you.  Worked like a champ.

---

