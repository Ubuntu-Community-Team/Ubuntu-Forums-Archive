---
title: "Internett connection problem with Kubuntu"
date: 2006-08-16
forum: Desktop Environments
---

### Post by trommas on 2006-08-16
Hi!

Winxp and ubuntu (dapper) connects properly to the net, but kubuntu won't!

It's strange really... I'm new to kubuntu (ubuntu never caused this), so I would appreciate any help :)

---

### Post by murataht on 2006-08-16
open a terminal (konsole in kde, i think). and i assume your interface is eth0 here.

 ```
sudo ifconfig eth0
```

check what it says: ip address, or other things. and then do:

```
sudo ifdown eth0
sudo ifup eth0
```

then check the output. maybe it could be fixed this way. but here i did a few assumptions: you are using a ethernet card, no wifi, no dail-up, or no others. 

if you can't fix it with the above method, try to provide more information regarding to your internet connection: like how it connects to the internet, what is the interface, what is the error output etc. more inofrmation better than nothing.:) 

good luck.

Murat

---

### Post by trommas on 2006-08-17
Thanks for the help!

I've added a snapshot of the terminal output and konqueror displaying a page :)

Is there any startup-script I have to edit to make this work permanently?

---

### Post by murataht on 2006-08-17
so, this fixed the problem. (from the pix, it says you have an ip address now)

about the startup script, it should be in /etc/init.d/networking. but this is the script that ubuntu and kubuntu both should run during boot up...

i really don't know where to add extra startup script. hope someone could help here or give a better solution for kde.

Murat

---

