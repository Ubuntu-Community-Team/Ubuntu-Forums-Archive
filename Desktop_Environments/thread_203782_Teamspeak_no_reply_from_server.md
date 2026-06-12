---
title: "Teamspeak: no reply from server"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Eddy Gordo from Tekken on 2006-06-25
first, i am new to linux.  self teaching through these forums, interweb, couple of books, a tuturial from work, and friends who claim to know things...

problem
i installed teamspeak server on ubuntu 5.10, configed the router,   got it working for me and my friends.  then, i started on a diff project, to set up a network with my ubuntu comp and my xp comp (FYI, i failed).  i had been using the same user name on both comps, so i decided to distinguish the linux box by changing the user name. so i used usermod to change the name and home directory of my user account. i mention all this because its the only thing i remember doing between the server working and not working.

now, when i

./teamspeak2-server_startscript start

the server stars with no errors in the terminal, howver when players try to join they get a no reply from server error.  so i checked the log. there is a series of errors that filenotfound

/home/new_login/Desktop/tss2_rc2/httpdocs/favicon.ico

plan A was to use synaptic to unistall and do it again from the beggining.  but it doesn't appear in synaptic.  Plan B was create favicon.ico.  that got rid of the error, but didn't allow others to connect still.  Plan C is this this forum.  thats all i can think to offer...  Thanks in advance.

---

### Post by Eddy Gordo from Tekken on 2006-06-28
i fixed it, router wasn't set up properly.  thanks for all the help.

---

### Post by xyz on 2006-06-28
[QUOTE=Eddy Gordo from Tekken]i fixed it, router wasn't set up properly.  thanks for all the help.[/QUOTE]

Check this out > To all those with zero-reply threads...
[http://ubuntuforums.org/showthread.php?t=82471](http://ubuntuforums.org/showthread.php?t=82471)

---

