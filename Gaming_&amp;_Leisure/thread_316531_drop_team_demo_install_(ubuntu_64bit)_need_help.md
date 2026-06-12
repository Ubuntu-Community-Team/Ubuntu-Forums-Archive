---
title: "drop team demo install (ubuntu 64bit) need help??"
date: 2006-12-10
forum: Gaming &amp; Leisure
---

### Post by slyjelly on 2006-12-10
hi,

i have been trying to get this demo (dropteam) working for over a week, 
the installation has worked, now i just wish to run the game

when doing this with the following command:

~/DropTeam$ sudo sh runClient.sh


this error comes up:

runClient.sh: 2: pushd: not found
runClient.sh: 3: ./SpaceVikings: not found

i cant find any other forum with this error message

any ideas? have you come accross this problem before?

any information would be helpful

im running ubuntu 64bit edgy with nvidia

thanks

---

### Post by slyjelly on 2006-12-12
anyone?](*,)

---

### Post by Phonan on 2007-11-26
Well, I'm really sorry and I doubt that you'll *cough* even be checking this thread anymore, but here's how you can get it to work. First, open the runClient.sh file in gedit, then change the second line to say:
```
cd /*DROPTEAMDIRECTORY*/bin
``` Replace the *DROPTEAMDIRECTORY* with the full path to wherever the DropTeam runClient.sh script is. For example, mine is at /home/user/DropTeam. 

If this doesn't work, don't despair! Change the first line to say ```
#! /bin/bash
``` and you'll be set. Good luck with the game!

---

