---
title: "running processes ."
date: 2008-12-10
forum: General Help
---

### Post by aboud on 2008-12-10
many tools can show you all running processes on your system, among them **top** and **htop**, where can I find more information about each of them ?

---

### Post by ajcham on 2008-12-10
[FONT="Fixedsys"]man top
man htop[/FONT]

---

### Post by binbash on 2008-12-10
man ps

---

### Post by aboud on 2008-12-10
upps I didn't elaberot .. by them i mean the processes , i know well these things . :popcorn:

---

### Post by ajcham on 2008-12-10
What are you hoping to learn about the processes?

---

### Post by aboud on 2008-12-10
which of them is crucial for the systme to work, for example lately i new the **tracked** is indexing serves, after i stopped it the computer begin working much better. but some time it slow down for reasons I don't know.

---

### Post by aboud on 2008-12-10
like now for example .. it take 30 40s to begin video..
other times it works very very fast .. :confused:

i recorded the process running immeditely after start up, and compared with those running at slow time, even tho i stopped the extra of them i don't now nothing changed.., i'm trying without running any programm.

---

### Post by ajcham on 2008-12-10
When I want to know if it's OK to disable a process, I usually turn to Google.  I found this to be the most reliable, because even if I know the purpose of a process, and conclude that I don't require it, other programs (which, on the face of it, seem unrelated) turn out to be dependent on the process in question.

> i recorded the process running immeditely after start up, and compared with those running at slow time, even tho i stopped the extra of them i don't now nothing changed.., i'm trying without running any programm.

Have you checked your resource use at the time?  Depending on how much RAM you have, resources may be backed up, with a lot of swapping.

---

### Post by aboud on 2008-12-10
don't think so, i have 2GB and used memory never went over 1200M
and i have other 2GB swap which i never noticed it's in use. :)

there should exsit some where list of essential processes, to keep the system alive, after all you know what you are using yourself, i mean for ex 
firefox
amarok

like this **tracked**, it's obviously extra, well you can run it when you need to find something. or once a day then turn it off.

---

