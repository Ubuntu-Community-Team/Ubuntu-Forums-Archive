---
title: "Could not update file /home/&lt;user&gt;/.ICEauthority (update solve)"
date: 2011-01-05
forum: Desktop Environments
---

### Post by MiCK.ca on 2011-01-05
Just recently I started encountering the annoying ".ICEauthority" error. After trying EVERY "solved" solution i could find here in these forums and others, I stumbled on a fix that is (IMHO) the only failsafe fix.

Another completely unrelated forums over at a broadband forum/linux forum said the culprit was veetle!  While i'm sure that others have never installed veetle and still have this annoying error; the more important thing here is the fix that fixed my error!

[SOLVED]

1. reboot into recovery mode
2. login in as root
3. use this command chown <user>:<user> /home/<user>
4. reboot 

error gone!

This leads me to believe that the error is caused by some rouge program changing the ownership of you home directory. Merely changing the file ownership isn't enough. you have to rid yourself of the program or cause first and then take ownership of your home again. 

hope this helps some head banging person with the same unsolved issue. 
now i'm rocking again!!!:guitar:

---

### Post by MiCK.ca on 2011-01-05
BTW..

The same forum had a fix for how to install Veetle so that you don't get the error...

*My thought is that if any site/ program/ programmer can't take the time to fix their software or plugin to work properly without having to jump through hoops to get it working; it shouldn't be installed on any Linux PC...* (someone in the forum was bashing Linux as being the problem)

[my two cents]

---

