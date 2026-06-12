---
title: "Help with few terminal things plz"
date: 2005-09-10
forum: Desktop Environments
---

### Post by kennny2004 on 2005-09-10
K Well i installed ubuntu server on my server pc and trying to run few things from it like one gameing server and another one my questions are:
1.How to make a shortcut or something that will make one very big line of starting my server simpler
2.How to switch between the servers and see what is running ( i mean like if it is in terminal and i start one server it will run it but how i leave it running and run another one and then switch between them. thanks

---

### Post by Daniel G. Taylor on 2005-09-10
1. You can create a simple shell script file, save it, and make it executible. Example:
```
#!/bin/bash

# This is a comment and below are a few commands
echo "Hello world!"
```
You can save that into a file and "chmod +x filename" to make it executable, then run it and any commands you put into the file will be executed. Search for a Bash scripting tutorial if you want to know more about what all you can do in shell scripts.

2. There is a utility called "screen" that will let you do just that in a terminal. You can install it with "apt-get install screen". A simple example of usage:
```
terminal$ screen
terminal$ gameserver
* let's pretend the game server just started*
* press Ctrl-A then D to detach from the screen*
terminal$ screen -x
* you will attach to the screen and see the game server*
* press Ctrl-A then D again*
terminal$ screen
* another new screen session starts*
* press Ctrl-A then D again*
terminal$ screen -list
There are screens on:
        15835.pts-0.Hostname      (Detached)
        15847.pts-0.Hostname      (Detached)
terminal$ screen -x 15835
* you attach to the first screen again*
* Ctrl-A then D to detach*
terminal$ screen -x 15847
* you attache to the second screen again*
```

Type "man screen" for more information.

---

### Post by jworr on 2005-09-11
crtl + alt + f1 ... f2 ... f3 will switch you between terminals and if you have X running it is f7

use the command "ln" to make links

---

