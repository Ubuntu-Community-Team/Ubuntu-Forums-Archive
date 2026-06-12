---
title: "how do you install games from cd ?"
date: 2007-02-15
forum: Gaming &amp; Leisure
---

### Post by techno-mole on 2007-02-15
hello
this is a very daft question, but how do you go about installing games from a disc ? when you stick a disc in the drive it shows up on the desktop, but how do you get it to install ?
cheers.

---

### Post by frodon on 2007-02-15
Which game, windows version linux version ?

Sorry but with so few informations impossible to answer.

---

### Post by techno-mole on 2007-02-15
sorry for the lack of info.
i have a game called descent 3 for linux, and im also thinking about getting doom 3, anyway back to descent 3, its on 3 cd's the third being an expansion pack, according to the install instructions this is what i need to do to install it - Mount the Descent 3 CD and change the current directory to where
it is mounted. Type 'sh setup.sh' to run the install script.

e.g.  Log in as root:
  $ mount /mnt/cdrom
  $ cd /mnt/cdrom
  $ sh setup.sh
now i must be doing something wrong because it doesnt seem to work ?

---

### Post by vantom on 2007-05-07
> **techno-mole said:**
> 
e.g.  Log in as root:
  $ mount /mnt/cdrom
  $ cd /mnt/cdrom
  $ sh setup.sh
now i must be doing something wrong because it doesnt seem to work ?
insted of $ sh setup.sh just do 
$ sudo bash setup.sh
it's gonna work this time

---

### Post by techno-mole on 2007-05-25
tried the commands like you said, and it still doesnt work.
cheers for the help though.

---

### Post by DarkN00b on 2007-05-25
Try ./setup.sh

---

### Post by Cappy on 2007-05-25
Ubuntu mounts to /media/ (not /mnt)

```

cd /media/cdrom
sudo sh setup.sh

```

Also, please post any errors you recieve when you try a suggestion and it doesn't work. No one can help you otherwise.

---

