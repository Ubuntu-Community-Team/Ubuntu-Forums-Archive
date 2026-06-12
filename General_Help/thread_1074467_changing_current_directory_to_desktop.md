---
title: "changing current directory to desktop?"
date: 2009-02-19
forum: General Help
---

### Post by abhilashm86 on 2009-02-19
i'm installing a software that is in tar.bz2 form, i extracted here, then i saw install file,

it told to change to current directory to desktop and then proceed.......

i know cd command,how to point it to desktop??

abhilash@abhi:~$ cd ~/desktop
bash: cd: /home/abhilash/desktop: No such file or directory
abhilash@abhi:~$ cd /home/abhilash/desktop
bash: cd: /home/abhilash/desktop: No such file or directory
abhilash@abhi:~$ cd /home/abhilash/desktop/
bash: cd: /home/abhilash/desktop/: No such file or directory

all errors,how to change pwd it to desktop??

---

### Post by sisco311 on 2009-02-19
linux is case sensitive; ~/desktop != ~/Desktop
```
cd ~/Desktop
```;)

---

### Post by abhilashm86 on 2009-02-19
oh got it,thanks, i noticed D capital in desktop which i din't do:)

---

