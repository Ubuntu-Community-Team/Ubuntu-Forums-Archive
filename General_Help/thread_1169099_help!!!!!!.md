---
title: "help!!!!!!"
date: 2009-05-24
forum: General Help
---

### Post by philcamlin on 2009-05-24
hi im in ubuntu 9.04 and everytime i go to install something  i get 
- dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

how do i fix this i have no idea what it mwans im a beginner so help ? :)

even sudo apt-get update gives me this

---

### Post by thegreenblob on 2009-05-24
Have you tried running:

```
sudo dpkg --configure -a
```

in a terminal? ;)

---

### Post by philcamlin on 2009-05-24
whats it suposed to dfo ?
wil it fix everything?

---

### Post by philcamlin on 2009-05-24
lol it worked :)

thanks

---

### Post by fballem on 2009-05-24
To access a Terminal, use Applications > Accessories > Terminal. Once it is open, it will show you a command prompt. The command prompt will look like username@computername:~$

Type the command _exactly_ as shown.

The command is sudo dpkg --configure -a

Once you have typed the command, press the enter key. You will be asked for your password, which you should type, then hit the enter key. You will not see your password displayed!

Things will happen and the problem will be corrected. You will know you are done when you return to the command prompt.

---

### Post by sailthesea on 2009-05-24
That is the magic of terminal:D

---

