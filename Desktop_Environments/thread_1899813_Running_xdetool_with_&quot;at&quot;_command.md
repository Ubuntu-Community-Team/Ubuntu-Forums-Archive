---
title: "Running xdetool with &quot;at&quot; command"
date: 2011-12-24
forum: Desktop Environments
---

### Post by unckybob on 2011-12-24
I am trying to send a "space" to a google chrome window running pandora. I want it to wake me up in the morning. I have a short file called "test" containing the following: 

sleep 2
xdotool key space

If I just run:

# bash test

or

# sh test

at the terminal and make the chrome window active a "space" is sent to the chrome window and it pauses. But I can't seem to make it work using the "at" command. The command:

# at now +1 min < test

doesn't do anything to the chrome window. Also I've tried:

# at now +2 min
warning: commands will be executed using /bin/sh
at> bash Mouse_Programming.txt
at> ^D

and

# at now +1 min 
warning: commands will be executed using /bin/sh
at> xdetool key space
at> ^D

and that doesn't do anything either. Can someone please help?

---

### Post by erind on 2011-12-24
'***at****'* command runs in a limited environment and the DISPLAY variable is not set, so *xdotool* does not have a terminal to send the command to. Edit your script **test.sh** like so:

```
#!/bin/bash

 [COLOR=Red]export DISPLAY=:0.0 [/COLOR]
 sleep 2
 xdotool key space

```Running it as: 

```
$ at now +1 min < test.sh
```Check this thread for a similar situation:

[http://ubuntuforums.org/showthread.php?t=608212&page=2](http://ubuntuforums.org/showthread.php?t=608212&page=2)

---

### Post by unckybob on 2011-12-24
That did it! Hurrah! Thanks so much. When I get further along in shell programming I'll probably figure out why. Awesome!

---

