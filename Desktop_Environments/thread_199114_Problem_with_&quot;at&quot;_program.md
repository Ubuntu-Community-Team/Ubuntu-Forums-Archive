---
title: "Problem with &quot;at&quot; program"
date: 2006-06-18
forum: Desktop Environments
---

### Post by matezz on 2006-06-18
Hello!!
Ive got problem with the "at" program: 
Example: I want to run glxgears at now +1minute: I type at now +1 minute, press enter, type glxgears and ctrl+d:

> $ at now +1 minute
warning: commands will be executed using /bin/sh
at> glxgears<EOT>
job 12 at Sun Jun 18 15:34:00 2006
$

Everything looks ok. but the action just doesn`t start.
I`ve checked the /etc/at.deny and /etc/at.allow files, the atd daemon is running. What am I doing incorrectly? Thanks :D

---

### Post by Ramses de Norre on 2006-06-18
It's not a real solution but for just making glxgears start in a minute you could use ```
if sleep 60; then glxgears; fi
```

---

### Post by matezz on 2006-06-18
Thanx, that works :)
I need it for downloading files at night, this could help.

---

### Post by sopo_dan on 2006-06-18
i had the exact same problem with at. but i didn't really need it, was just playing around so i didn't give it much thought
but i'd also be interested in a solution

---

### Post by matezz on 2006-06-20
I have got the solution,  I got it from guys on the Czech Ubuntu forum ([http://forum.ubuntu.cz/viewtopic.php?pid=13625#p13625](http://forum.ubuntu.cz/viewtopic.php?pid=13625#p13625)) 
At has to be told where the X runs:

$ at now +1 minute
warning: commands will be executed using /bin/sh
at> DISPLAY=:0 glxgears
at> <EOT>
job 1 at Tue Jun 20 21:28:00 2006

and it runs :)

---

