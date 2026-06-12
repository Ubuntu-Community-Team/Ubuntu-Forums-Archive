---
title: "how to install program .bin ?"
date: 2009-07-09
forum: Desktop Environments
---

### Post by tonjaa on 2009-07-09
i try to download program and save at Desktop  but it's .bin file  name      [COLOR=DarkOrange]CollanosPhoneInstaller.bin[/COLOR] 
how i can install from terminal ? please guide me by step.

---

### Post by wojox on 2009-07-09
Open a terminal

```
cd /Desktop
```

```
chmod 755 CollanosPhoneInstaller.bin 
```

Then

```
./CollanosPhoneInstaller.bin
``````

```

---

### Post by tonjaa on 2009-07-09
:p thank you so much now i can installed .[COLOR=Green] work![/COLOR]

---

### Post by loweehahn on 2009-08-03
I tried typing cd /Desktop but what I get is:

kelvin@ubuntu:~$ cd /desktop
bash: cd: /desktop: No such file or directory

---

