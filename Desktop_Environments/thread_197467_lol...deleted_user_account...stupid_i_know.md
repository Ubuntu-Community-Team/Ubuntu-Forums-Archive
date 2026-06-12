---
title: "lol...deleted user account...stupid i know"
date: 2006-06-15
forum: Desktop Environments
---

### Post by hoehaver on 2006-06-15
ok i had a second hard drive that wasnt mounted so i was going to mount it so i went to system>adm.>disk and i went to the partitions tab and on the brouse button(so you can brouse to the folder you want the folders to be placed at)and i wanted the folders to be in "home" but when i selected home, the folder inside of home (john) was highlighted. i didnt want it in john so i just selected john and it showed up as something like "/home/john" so i just deleted the john part and left it like "home/" there may have been a word before home but im not sure, i forget. and a friend told me i deleted my account and i cant access anything i cant even log on as root. i tryed root, and my password and sudo and mypassword but nothing works i cant even log on ubuntu it says the session lasted for less than 10 seconds, does anyone know how to create a new account  in failsafe termanel (if the failsafe termanel will work) i havent tryed it yep.

---

### Post by IYY on 2006-06-15
adduser is the command you use. It's fairly simple to figure out, just answer the questions it asks you. Make sure you make this new user you add a member of the 'admin' group.

---

### Post by hoehaver on 2006-06-16
well when i did that i typed 
sudo adduser johnathan, and when i did it went ahead and made johnathan a new user but it also made a group called johnathan, what do i type after johnathan to make him an administrator or...how do i acomplish this

---

### Post by Ramses de Norre on 2006-06-16
```
adduser johnathan admin
```

---

