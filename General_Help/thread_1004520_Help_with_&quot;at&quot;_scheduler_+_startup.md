---
title: "Help with &quot;at&quot; scheduler + startup"
date: 2008-12-07
forum: General Help
---

### Post by CJay554 on 2008-12-07
Alright, so i've been messing around with at to figure out how to stop transmission at a certain time every morning, around 6:00 AM.

i seem to be having some odd problems...

if i do 

at now
killall transmission
^D

it immediately kills transmission (as expected)

but if i set it at a certain time it doesn't kill it at all. like if i set it for 2 minutes from now..

I used to be able to do this no problem.
At some point also i would like to add this command at startup so i don't have to re-enter it every night.

I think it might have something to do with the at.allow/at.deny in the /etc/ directory, but im not sure how to edit those.

Thanks for any help!

[ADD]
sudo at <time>
killall transmission

This seems to work (sometimes), however i would like to run it as a regular user.

---

### Post by spupy on 2008-12-07
A tip: You should be able to close transmission with this command:
```
transmission-remote --type gtk --quit
```
(but it doesn't work here on my gentoo for some reason.)

---

