---
title: "Modify the MAXCLIENTS variable in Xubuntu"
date: 2018-03-20
forum: Desktop Environments
---

### Post by buryusadu on 2018-03-20
Hello, I want to have a lot of programs opened at the same time, when i open about 50, i get this error:

```
"Maximum number of clients reached"
```

I found that modifying the MAXCLIENTS variable in **/usr/include/xorg/misc.h** Can let me open more processes, but that file doesn't exists in Xubuntu.

I'm using Xubuntu 16.04 LTS

Thanks in advance for the help.

---

### Post by kerry_s on 2018-03-20
50? i believe you can just create the file.

i don't even have that many apps. lol

---

### Post by Holger_Gehrke on 2018-03-21
It would surprise me very much if the value of a constant in a file that's meant to be included during the compilation of client programs had any influence on the running server without recompiling the server. There is an option MaxClients you can put into the Serverflags section of the xorg.conf which should do what you want. See the manual page ('man xorg.conf') for the details.

Holger

---

### Post by buryusadu on 2018-03-21
I figured how to do it

I had to install **xserver-xorg-dev**

then the file is finally in [B]/usr/include/xorg/misc.h
[/B]
and increasing the MAXCLIENTS variable works perfectly so i solved my problem.

---

