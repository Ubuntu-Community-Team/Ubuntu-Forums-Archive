---
title: "&quot;Could not find a usable uninstall program. Aborting&quot;"
date: 2006-08-15
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-08-15
What does this mean?

---

### Post by simonn on 2006-08-15
Not know what you were doing, I would say it means something could not find a usable uninstall program so aborted.

---

### Post by WalmartSniperLX on 2006-08-15
Im trying to uninstall a game but not sure what to do. I get that when i type in the command to remove using the uninstall

---

### Post by maniacmusician on 2006-08-15
did you install it using make? if so, have you tried just doing

sudo make uninstall

?

---

### Post by WalmartSniperLX on 2006-08-15
> **maniacmusician said:**
> did you install it using make? if so, have you tried just doing

sudo make uninstall

?

lol not sure (thanks for posting) lemme do that

---

### Post by WalmartSniperLX on 2006-08-15
I did this and got:

patrick@patrick-desktop:~$ cd /usr/local/games/armyops
patrick@patrick-desktop:/usr/local/games/armyops$ sudo make uninstall
Password:
make: Nothing to be done for `uninstall'.

---

### Post by maniacmusician on 2006-08-15
hmm...well, how did you install the program in the first place? did you do it from source, or what?

---

### Post by petersjm on 2006-08-15
Did you apt-get or aptitude the install from the command line?

```
sudo aptitude install PACKAGE
```

If so, go back to the terminal and try

```
sudo aptitude purge PACKAGE
```

or 

```
sudo apt-get remove PACKAGE
```

Depending on whether you used apt-get or aptitude in the first place...

---

### Post by carontis on 2006-08-15
Well, apt-get remove *package* should be enough, but if not try using dpkg -r *Package*, or again going in Synaptic and check if it's there and remove it from there.

---

### Post by Al Biheiri on 2008-06-18
> **WalmartSniperLX said:**
> What does this mean?
try:

1- sudo su
2- ./uninstall

---

### Post by Heinstein on 2008-07-06
It worked
Thanks


:guitar:

---

