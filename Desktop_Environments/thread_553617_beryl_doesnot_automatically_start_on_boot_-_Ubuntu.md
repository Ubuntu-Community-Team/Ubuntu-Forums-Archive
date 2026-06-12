---
title: "beryl doesnot automatically start on boot - Ubuntu Feisty"
date: 2007-09-18
forum: Desktop Environments
---

### Post by bcdixit on 2007-09-18
Hi,
I have gone through the standard procedure of setting up beryl to start on boot but that does not seem to work. the way I set it up was through 
system --> preferences --> session
under startup programs I created a new entry as beryl and the command was also given as** ' beryl '.**

But when i boot my machine beryl doesnot load automatically. I have to open up a terminal window and start beryl manually.

Anybody has the same problem? any hints / solutions are welcome.

thanx
bcd

---

### Post by misfitpierce on 2007-09-18
try downloading beryl-manager

sudo apt-get install beryl-manager

then start beryl-manager under settings under app's.

then hit sessions... add beryl-manager and switch over and save current session
then CTRL+ALT+BCKSPC and see if it worked... Good luck :)

---

