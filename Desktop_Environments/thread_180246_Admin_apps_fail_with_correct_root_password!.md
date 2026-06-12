---
title: "Admin apps fail with correct root password!"
date: 2006-05-21
forum: Desktop Environments
---

### Post by cebaehren on 2006-05-21
PC: Siemens Nixdorf FD210M6 (multimedia PC with TV decoder, all in one monitor & case) 64 MB RAM (100 % OK) hd 6GB:1,8 GB Win, 250MB swap, 3 GB ext3 /, 1,5GB /home, runs in windows OK!
Ubuntu 5.04 original CD!
"Admin" applications prompt for root password, I type it, 
then **error: wrong password**
In virtual terminals and terminal emulation my root password is accepted!, (but not in root terminal!). I changed it with #passwd in virtual term, but allways the same: wrong password for admin applications under gnome
Then I installed ubuntuaddon (112 MB)in the hope is a bug and
Again the try to administrative needs in  the installed Linux:
"Admin" applications prompt for root password, I type it, then the prompt disappear, then nothing.... When i try to relaunch a "admin" application i get: **Failed to run ######: the Child terminated with 1 status**. 
I guess its not a normal behavior, I have readed more than 10 hours guides Official and unofficial) and something else
anyone know what is the problem? 
And BIGGER: Is the same problem I have in an intel SR440 B# !!!!
I have in my other (normal) live a lot of intallations and configurations of other distros SuSE, Mandrake, Red Hat, Knoppix, etc; but Debian and UBUNTU are (relatively) new for me.
Ihave installed 3 or 4 times the Ubuntu PIG!
_extra note_: as standard user in the installation it does not accept a name e.g.:  B**ä**hren with  (Umlaut=dieresis) and 
in the root password if you make a typo  in the first line, the second try is not possible to correct (clicking <back> does not help!)
Who helps? 
thanks in advance!!!!
I accept ideas or solutions for my big problem in english, german, spanish, portuguese, french or italian language! (but precise or exact terms, please!)
gracias!
Carlos Enrique Bähren, Santa Cruz de la Sierra, Bolivia

---

### Post by cebaehren on 2006-05-21
PC: Siemens Nixdorf FD210M6 (multimedia PC with TV decoder, all in one monitor & case) 64 MB RAM (100 % OK) hd 6GB:1,8 GB Win, 250MB swap, 3 GB ext3 /, 1,5GB /home, runs in windows OK!
Ubuntu 5.04 original CD!
"Admin" applications prompt for root password, I type it, 
then **error: wrong password**
In virtual terminals and terminal emulation my root password is accepted!, (but not in root terminal!). I changed it with #passwd in virtual term, but allways the same: wrong password for admin applications under gnome
Then I installed ubuntuaddon (112 MB)in the hope is a bug and
Again the try to administrative needs in  the installed Linux:
"Admin" applications prompt for root password, I type it, then the prompt disappear, then nothing.... When i try to relaunch a "admin" application i get: **Failed to run ######: the Child terminated with 1 status**. 
I guess its not a normal behavior, I have readed more than 10 hours guides Official and unofficial) and something else
anyone know what is the problem? 
And BIGGER: Is the same problem I have in an intel SR440 B# !!!!
I have in my other (normal) live a lot of intallations and configurations of other distros SuSE, Mandrake, Red Hat, Knoppix, etc; but Debian and UBUNTU are (relatively) new for me.
Ihave installed 3 or 4 times the Ubuntu PIG!
_extra note_: as standard user in the installation it does not accept a name e.g.:  B**ä**hren with  (Umlaut=dieresis) and 
in the root password if you make a typo  in the first line, the second try is not possible to correct (clicking <back> does not help!)
Who helps? 
thanks in advance!!!!
I accept ideas or solutions for my big problem in english, german, spanish, portuguese, french or italian language! (but precise or exact terms, please!)
gracias!
Carlos Enrique Bähren, Santa Cruz de la Sierra, Bolivia
[email]cebaehren@gmail.com[/email]

---

### Post by aysiu on 2006-05-21
Two questions.

Have you read this?
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Did you do an **expert** install?

---

### Post by codejunkie on 2006-05-21
[QUOTE=cebaehren]PC: Siemens Nixdorf FD210M6 (multimedia PC with TV decoder, all in one monitor & case) 64 MB RAM (100 % OK) hd 6GB:1,8 GB Win, 250MB swap, 3 GB ext3 /, 1,5GB /home, runs in windows OK!
Ubuntu 5.04 original CD!
"Admin" applications prompt for root password, I type it, 
then **error: wrong password**
In virtual terminals and terminal emulation my root password is accepted!, (but not in root terminal!). I changed it with #passwd in virtual term, but allways the same: wrong password for admin applications under gnome
Then I installed ubuntuaddon (112 MB)in the hope is a bug and
Again the try to administrative needs in  the installed Linux:
"Admin" applications prompt for root password, I type it, then the prompt disappear, then nothing.... When i try to relaunch a "admin" application i get: **Failed to run ######: the Child terminated with 1 status**. 
I guess its not a normal behavior, I have readed more than 10 hours guides Official and unofficial) and something else
anyone know what is the problem? 
And BIGGER: Is the same problem I have in an intel SR440 B# !!!!
I have in my other (normal) live a lot of intallations and configurations of other distros SuSE, Mandrake, Red Hat, Knoppix, etc; but Debian and UBUNTU are (relatively) new for me.
Ihave installed 3 or 4 times the Ubuntu PIG!
_extra note_: as standard user in the installation it does not accept a name e.g.:  B**ä**hren with  (Umlaut=dieresis) and 
in the root password if you make a typo  in the first line, the second try is not possible to correct (clicking <back> does not help!)
Who helps? 
thanks in advance!!!!
I accept ideas or solutions for my big problem in english, german, spanish, portuguese, french or italian language! (but precise or exact terms, please!)
gracias!
Carlos Enrique Bähren, Santa Cruz de la Sierra, Bolivia[/QUOTE]
ubuntu uses sudo/gksudo to execute the admin applications, when your prompted for the password, enter the password of the first user you created when installing ubuntu. if you did an expert install try this post [http://ubuntuforums.org/showpost.php?p=841225&postcount=12](http://ubuntuforums.org/showpost.php?p=841225&postcount=12)
it will show you how to add your name to the sudoers file, then it should accept your user password.

---

### Post by frodon on 2006-05-22
merged

---

