---
title: "Login Problem"
date: 2006-08-17
forum: Desktop Environments
---

### Post by anup09 on 2006-08-17
Well i jus installed yesteday dual boot Ubuntu with XP.. it all worked fine until i updated all the files in ubuntu.. the total update package was about 184MB i think.. well i set that to run and i left my computer and when i got back to it in about 1 hr it had a  screen of something like a space sation and a canada flag i think if i remember correctly.. well it was frozen so i decided to turn it off by holding down the power button for 10 seconds.. later i tried to get back into ubuntu the login screen comes up and everthing loads but when i imput my username and password it goes to some black screen then comes and assks me again...

???

i kno its teh correct password cause when i imput the ronge pass it tells me its incorrect.. so i dont kno..

>>>???

P.S Im a newb to linux

---

### Post by murataht on 2006-08-17
from the symptoms, it seems like the x is broken, or something related to x. this must be related to your unfinished upgrade. maybe finish the upgrade should fix the problem. 

ctrl+alt+F1 (or F2,F3,..,F6)

you will be in a console, login with your username and password. 

type
```
sudo apt-get update
sudo apt-get upgrade
```

this should finish rest of the upgrade hopefully. then try reboot, and login. 

if this does not fix the problem, maybe fix the x configuration will fix it. or simpler, a fresh new install. 

good luck

Murat

---

### Post by anup09 on 2006-08-17
Thx but in order for that to work do i have to be in recovery mode.. ??? i can get in then maby login then run that command..

---

### Post by Redache on 2006-08-17
> 
ctrl+alt+F1

I'm pretty sure that's the key shortcut for command line. It does sound like a dodgy update, like files are half updated so they won't actually load.

---

### Post by mssever on 2006-08-17
> **anup09 said:**
> Thx but in order for that to work do i have to be in recovery mode.. ??? i can get in then maby login then run that command..
You can use recovery mode if you want, but if you use the keyboard shortcuts above, you can probably save a little time and a reboot or two.

---

### Post by anup09 on 2006-08-17
when i try it it says .. E: dpkg was interupted, you must run dpkg --configure -a to correct the prob.. when i do that says unsupported command

---

### Post by anup09 on 2006-08-17
hmmmmm

---

### Post by murataht on 2006-08-17
did you do it with sudo?

for example:
```
sudo dpkg --configure -a
```

---

### Post by anup09 on 2006-08-17
> **murataht said:**
> did you do it with sudo?

for example:
```
sudo dpkg --configure -a
```



Well i was forgetting it but then i put it in and it did some crap and updated some crap..

then it froze again so i had to force a shut down and i did.. then restarted and when i log back into that ctrl alt f1 adn type that command it doesnt do anything.. and when i try the apt update and upgrade commands they pull up crap but 1 sticks at downloaded at 0/58.__MB and the other jus sticks at some http address.. well it looking like i mite need to do clean restore.. which is not that much of a problem but i hate doing it.. so if i find a solution before school finishes tommz ill use that or its gonna be a clean resotre..

---

### Post by anup09 on 2006-08-18
Problem Solved for me.. i put in my live cd and found that my ubuntu partition was only done for 2GB .. Wonders.. i only had 46 MB left and the update was about 133MB.. :) so im happy now.. im currently on it.. jus bout to update..

---

### Post by murataht on 2006-08-18
good luck!

---

