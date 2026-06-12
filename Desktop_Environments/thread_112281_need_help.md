---
title: "need help"
date: 2006-01-04
forum: Desktop Environments
---

### Post by mike123456 on 2006-01-04
i am new to linux and have tried to learn how to use the terminal window many times to install programs but not getting anywhere ,this is becoming very frustrating,i like linux very much and dont really want to go back to spyware and windows lol,is there another way to install programs without using terminal,i did try to use add program section for amsn 095 but it gave me the old versoin,i also tried auto update to ubuntu now my sound is gone after i put in updates.can anyone show me how to install amsn 095 and actually run it,i did install it and files were all there loaded in home folder but i could not start amsn,i did follow instructions giving to install it and cut and pasted those but nothing worked,i also installed other files they said i needed to run it,still nothing works.i am using ubuntu breezy badger 5.10 Is there any linux that allready has amsn or anywebcam messenger installed?man my fingers are sore.

---

### Post by darth_vector on 2006-01-04
ok. with the terminal you can get updates by running
```
sudo apt-get update
sudo apt-get dist-upgrade
```
and you can install programs by running
```
sudo apt-get install programname
```

if you dont like the terminal you can use a program called synaptic to update your system and install new programs. it is in the gnome menu somewhere (i cant tell you where because i uninstalled it).

---

### Post by hobbit1983 on 2006-01-04
Synaptic can be found in the gnome menu:

System -> Administration -> Synaptic Package Manager

It will prompt you for a password just type your logon password.

From this you can search the software available for ubuntu and then install it.

---

### Post by Sef on 2006-01-04
When using apt-get, make sure you are exact in what you type.  If you are off, even with an extra space, you will get an error message.  I do like using it, but at times it does get a bit frustrating until I realize what I am mistyping.

---

