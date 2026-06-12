---
title: "mpx, a new problem"
date: 2008-07-17
forum: Desktop Environments
---

### Post by schmidtbag on 2008-07-17
first of all, for those of you who don't know what mpx is.... well i'd rather not explain it, just check out the video here:
[http://gizmodo.com/gadgets/touch-me/linux-mpx-multi+touch-table-may-become-free-diy-microsoft-surface-one-day-278613.php](http://gizmodo.com/gadgets/touch-me/linux-mpx-multi+touch-table-may-become-free-diy-microsoft-surface-one-day-278613.php)


i have noticed other posts about mpx, but none of them really mentioned how to install it.  i searched on google and found this:
[http://wearables.unisa.edu.au/mpx/?q=node/85](http://wearables.unisa.edu.au/mpx/?q=node/85)
which does install mpx on ubuntu.  but, thats as far as i got.  i have no idea how to configure it or how to start it.

after running "sudo apt-get install mpx", the other functions given didn't work.  so, does anybody know how to get anywhere with this?

i am aware that i'm supposed to edit /etc/X11/xorg.conf, which i was capable of doing, but when i tried adding the other mouse, the next time i booted up my computer i just got in low graphics mode with no other results.

has anyone successfully got this to work in ubuntu?  i really don't get why there are nearly no answers on how to get this to work, i've searched for a couple hours

---

### Post by schmidtbag on 2008-07-18
nobody has mpx for ubuntu?

---

### Post by mali2297 on 2008-07-18
To continue with the instructions given in the link, I think you need to kill the X server first.

In a terminal window, type
```

sudo /etc/init.d/gdm stop

```
Then I you should get to a text console. From there, enter the next three lines:
```

export PATH=/opt/mpx/bin:$PATH
export LD_LIBRARY_PATH=/opt/mpx/lib:$LD_LIBRARY_PATH
xinit -- /opt/mpx/bin/Xorg

```

---

### Post by schmidtbag on 2008-07-19
oooh i never knew you had to kill xserver.  i'll go try that out, thanks.

---

### Post by schmidtbag on 2008-07-19
it didn't work.  when i typed the final line i was getting an error.  i can't remember exactly what it was but it mentioned something about /usr/bin and PATH, so i typed the following:

export PATH=/usr/bin:$PATH

and it seemed to have done something but i noticed no change.  now what?

---

### Post by brnetonboy on 2008-09-17
schmidtbag:
did you ever have success with this? I am sure a lot of people would appreciate it if you could post how you got it to work. there are about 20 unsolved threads on these forums where people are trying to get MPX to work...

---

