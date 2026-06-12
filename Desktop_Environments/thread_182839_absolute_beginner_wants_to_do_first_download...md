---
title: "absolute beginner wants to do first download.."
date: 2006-05-26
forum: Desktop Environments
---

### Post by pegasus on 2006-05-26
hi, i'm bald, fattish and airy; a breezy badger. i need to install firestarter to get rid of the hair, but have got stuck on 1/ what uncomment means and how to. and 2/ can anyone recommend a link which will provide idiot proof definitions therefore, and will walk me through this exiting time. you must have been there...

---

### Post by Sef on 2006-05-26
First go to this ubuntu site to add the repositories:

[How to add repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

Next do this:

Applications > Accessories > Terminal

then type in these two commands

sudo apt-get update (enter)

password [the password that you log in with] (enter)

After it finishes,

sudo aptitude install firestarter

---

### Post by Sutekh on 2006-05-26
Uncomment means to remove a '#' symbol from a configuration file, I'm assuming your /etc/apt/sources.list file, right?

Any line that starts with a # symbol is treated as a 'comment' not a command and ignored by applications that use the file.  Removing the # symbol, 'uncomments' the line.

Is there any particular link that you were following, that we could walk you through?  Were you enabling the so-called **universe** repository to install firestarter?

---

