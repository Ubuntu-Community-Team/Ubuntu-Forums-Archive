---
title: "need to make a program start automatically..."
date: 2009-04-20
forum: General Help
---

### Post by veda87 on 2009-04-20
I need to make a program to run as soon as i boot my system....
how can i do it....

i tried through ```
system->preference->sessions
add
```
then it asked for details and i gave these details ```
name: firefox
command: /home/veda/Desktop/firefox.desktop
comment: web browser
``` Then i restarted my system... but the firefox is not starting automatically...

Am i wrong in giving the data...If so, do correct me....

---

### Post by leandromartinez98 on 2009-04-20
The command should be: /usr/bin/firefox

In order to know the commands, type this in the command:

which firefox

or any other command. This will tell you the exact location of the 
corresponding program.

And you usually don't need to restart the system, just logout and login again.

---

### Post by Lunx on 2009-04-20
> **veda87 said:**
> I need to make a program to run as soon as i boot my system....
how can i do it....

i tried through ```
system->preference->sessions
add
```then it asked for details and i gave these details ```
name: firefox
command: /home/veda/Desktop/firefox.desktop
comment: web browser
``` Then i restarted my system... but the firefox is not starting automatically...

Am i wrong in giving the data...If so, do correct me....


For the command you don't need to write the path, just the app you wish to have run on startup, so instead of **command: /home/veda/Desktop/firefox.desktop**, just put in **firefox** and all should be wonderful with the world

---

