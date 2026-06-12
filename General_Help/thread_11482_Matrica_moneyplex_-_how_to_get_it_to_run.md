---
title: "Matrica moneyplex - how to get it to run?"
date: 2005-01-17
forum: General Help
---

### Post by alaska02 on 2005-01-17
I have installed moneyplex and when I do "./start", it won't start because of a missing lib.
And yes, I have installed the  libstdc++2.9-glibc2.1 2.91.66-4, as it is mentioned in the FAQ for debian-users at [www.matrica.de](www.matrica.de).
Did anyone out there get moneyplex to work with ubuntu?

Many thanx

Burkard

---

### Post by Kareema on 2005-01-17
What is the exact error message you get when starting moneyplex? When does moneyplex terminate (f.ex. before/after splash screen)?

---

### Post by alaska02 on 2005-01-20
Sorry for the delay!
But I attended the funeral of my uncle, so I was offline.
Now, I am at work and there is only Windows around, and of course no moneyplex.
So I will answer you in the evening.
I don't see the splash-screen, in the terminal moneyplex doesn't start at all, I only get the message "libstd..... is missing".
Bye
Burkard

---

### Post by alaska02 on 2005-01-20
So, now I am home and here is the message:


bubu@amiga:~/moneyplex $ ./start
/home/bubu/moneyplex/moneyplex: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

Does this help anyone?

Burkard

---

### Post by Kareema on 2005-01-21
Try making a symbolic link:
ln -s /usr/lib/libstdc++.so.x.x.x /usr/lib/libstdc++-libc6.1-1.so.2

First argument is the existing library in /usr/lib. You have to replace the x.x.x and look for the version you have installed (the first x should be a 6). The second argument is the name of the symlink.

I assume you are trying to run moneyplex on i386 and not on an amd64 architecture.

---

### Post by alaska02 on 2005-01-21
Hello, Kareema!

This was the right hint!
With the sym link it works!

Many thanks
Burkard

---

### Post by mattis on 2005-03-07
hi,
I want to start moneyplex as well, but I have a different problem: after installation, when trying to start the start-script I get the following message:

matthias@ubuntu:~/software$ ./start
chmod: Beim Setzen der Zugriffsrechte für ,,/home/matthias/software/moneyplex": Operation not permitted
Exception EFOpenError in Modul moneyplex bei 0807AC1B.
Datei /home/matthias/software/mdaten/Mandant.rdb kann nicht geöffnet werden.
./start: line 30:  9053 Segmentation fault      $APPPATH/$APPNAME

Looks like I don't have some kind of access-rights. Running it as root works fine, but I don't want to enter the net with a program running as root (in Suse it worked in user-mode anyway).
Any helpful suggestions?
mattis

---

### Post by Kareema on 2005-03-07
[QUOTE=mattis]hi,
I want to start moneyplex as well, but I have a different problem: after installation, when trying to start the start-script I get the following message:

matthias@ubuntu:~/software$ ./start
chmod: Beim Setzen der Zugriffsrechte für ,,/home/matthias/software/moneyplex": Operation not permitted
Exception EFOpenError in Modul moneyplex bei 0807AC1B.
Datei /home/matthias/software/mdaten/Mandant.rdb kann nicht geöffnet werden.
./start: line 30:  9053 Segmentation fault      $APPPATH/$APPNAME

Looks like I don't have some kind of access-rights. Running it as root works fine, but I don't want to enter the net with a program running as root (in Suse it worked in user-mode anyway).
Any helpful suggestions?
mattis[/QUOTE]

Good that you have switched to Ubuntu ;-)
OK, here we go: When you started moneyplex as root, it has changed the owner of some files/directories as it seems. Look at the owner of the files under the moneyplex directory: Some files should have the owner root or something else but not matthias as it should be. To change that type " sudo chown -R matthias:matthias /home/matthias/software/moneyplex/" to set the owner and group of all files and directories in the moneyplex directory recursively to matthias.

Hope this helps.

---

### Post by mattis on 2005-03-08
thanks a lot, I'm sorry to say that it did not do the trick though:
There still seems to be a problem with the starting script (which is also displayed below). The output was as follows

matthias@ubuntu:~/software/moneyplex$ /home/matthias/software/moneyplex/start.bash
Exception EFOpenError in Modul moneyplex bei 0807AC1B.
Datei /home/matthias/software/moneyplex/mdaten/Mandant.rdb kann nicht geöffnet werden.
/home/matthias/software/moneyplex/start.bash: line 30:  9714 Segmentation fault      $APPPATH/$APPNAME
matthias@ubuntu:~/software/moneyplex$ less start.bash
matthias@ubuntu:~/software/moneyplex$ more start.bash
#!/bin/bash

# Name und Pfad der Applikation
APPNAME=moneyplex
PRENAME=prestart
APPPATH=/home/matthias/software/moneyplex

# Pfad auf Existenz prüfen.
if [ ! -d $APPPATH ]; then
  echo "$APPPATH wurde nicht gefunden."
  exit 1
fi

# Applikation auf Existenz prüfen.
if [ ! -f $APPPATH/$APPNAME ]; then
  echo "$APPPATH/$APPNAME wurde nicht gefunden."
  exit 1
fi

cd $APPPATH

something seems to be wrong with the secondlast line of the script...any idea?
matthias

---

