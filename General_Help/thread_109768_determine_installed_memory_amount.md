---
title: "determine installed memory amount"
date: 2005-12-29
forum: General Help
---

### Post by missmoondog on 2005-12-29
simple question, i guess. where do i locate how much memory ubuntu is seeing. i justt added 256MB's to my system. it got some error booting windows, but ubuntu booted fine. i do believe i saw, as it was booting up, the 384MB's it has. (had 2/128MB sticks) i'm try to find where it shows the amount like windows does when you right click my computer.

thanks

---

### Post by kaamos on 2005-12-29
open gnome-system-monitor of use this command in terminal```
free -m
```Hope this helps.

---

### Post by missmoondog on 2005-12-29
wow! to fast!! helped perfectly, i think!!  does this look right? does to me, i think, again!! LOL

thanks

total       used       free     shared    buffers     cached
Mem:           377        372          5          0         13        204
-/+ buffers/cache:        153        223
Swap:          502          0        502

edit:
right as i posted that, ubuntu crashed and restarted. first time thats happened.

---

### Post by d11wtq on 2005-12-29
Here:

cat /proc/meminfo  #Look at the top line

Use this to cut out all the jibberish :P

cat /proc/meminfo | head -n 1  #One line answer

```
root@w3style:~# cat /proc/meminfo | head -n 1
MemTotal:       515704 kB
root@w3style:~#
```

EDIT | By the way... given the issue you had with windows you may want to run memtest86 ;)

---

### Post by tlc on 2005-12-29
```
top
``` - short'n'sweet...

---

### Post by missmoondog on 2005-12-29
thanks again. 
that issue i had was due to a bad stick of memory i had just added. put the old one back in and all is well again.

---

