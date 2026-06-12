---
title: "&quot;Invalid MIT-MAGIC-COOKIE-1 key&quot; when starting progams from terminal"
date: 2018-05-20
forum: Desktop Environments
---

### Post by drhex on 2018-05-20
Whenever I try to start (from a terminal) a program that requires graphics, I get "Invalid MIT-MAGIC-COOKIE-1 key" and the program won't start.
Using ubuntu 18.04 and this started to happen after I installed the proprietary Nvidia driver (as that reduces power consumption by 15W).
I can still start graphics programs by clicking icons.
Same problem for both ordinary user and root.
Googling suggests there is a problem with the ~/.Xauthority file. I have no such file, but it seems to have been replaced by something else:
```
echo $XAUTHORITY
/run/user/1000/gdm/Xauthority
```
That file certainly exists and contains the string MIT-MAGIC-COOKIE-1.

What is the next thing to try?

---

### Post by drhex on 2018-05-21
Found the problem: an ancient shell script file set the environment variable DISPLAY to :0.0  
When I let it remain at the default :1 it works again.

---

