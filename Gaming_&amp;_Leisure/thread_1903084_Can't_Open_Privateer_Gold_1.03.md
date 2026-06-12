---
title: "Can't Open Privateer Gold 1.03"
date: 2012-01-01
forum: Gaming &amp; Leisure
---

### Post by jabberwock_11 on 2012-01-01
Hi folks,

I am fairly new to Ubuntu, so this may be an easy thing to fix, but I dunno.  I am running Ubuntu 11.10 and I just downloaded Privateer Gold (PrivateerGold1.03.bz2.bin) and attempted to install it after changing the file permission to allow executing the file as a program.  I open a terminal and type "sudo sh PrivateerGold1.03.bz2.bin" only to get the error statement "sh: Can't open PrivateerGold1.03.bz2.bin"

I have looked at various forums and no one else seems to have this same issue, so I must be doing something pretty basic wrong.  I have also tried to run from root and get the same message.

Any suggestions would be really appreciated.

---

### Post by Perfect Storm on 2012-01-01
Try;

```
sudo ./PrivateerGold1.03.bz2.bin
```

Make sure you exit the installer when done, and not launch the game from it.

---

### Post by jabberwock_11 on 2012-01-02
Hey I got it!

Your command gave me the clue...the / part of it made me think that I just needed to be in the same directory as the file before attempting to run it.  As soon as I did a change directory command to the proper directory and THEN ran it, everything worked just fine.  I know this may sound pretty basic for most Linux users, but for someone coming from windows with only a basic idea of command line stuff, this was not something that I thought of right off the bat.  To be honest if I didn't know a bit about python and cmd in windows then I probably would not have even thought of it.

Thanks for the help.

---

### Post by oldrocker99 on 2012-01-02
> **Artificial Intelligence said:**
> Try;

```
sudo ./PrivateerGold1.03.bz2.bin
```

Make sure you exit the installer when done, and not launch the game from it.

Uh, shouldn't that be 
```
 sudo sh PrivateerGold1.03.bz2.bin
```
instead?

---

### Post by dez82 on 2012-10-20
> **oldrocker99 said:**
> Uh, shouldn't that be 
```
 sudo sh PrivateerGold1.03.bz2.bin
```
instead?

This is the correct answer!:popcorn:

All you others are just plain wrong

---

