---
title: "Peragro Tempus - Need Help Installing Pls"
date: 2008-01-17
forum: Gaming &amp; Leisure
---

### Post by mad chey on 2008-01-17
Been following the installation guide for gutsy, and all was well until i entered this

:/opt/peragro_svn/cal3d/cal3d$ autoreconf --install --force

and got this

Can't exec "aclocal": No such file or directory at /usr/bin/autoreconf line 182.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf line 182.
Can't exec "automake": No such file or directory at /usr/bin/autoreconf line 183.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf line 183.
Can't exec "aclocal": No such file or directory at /usr/share/autoconf/Autom4te/FileUtils.pm line 290.
autoreconf: failed to run aclocal: No such file or directory



ok im guessing it is a problem cos i tried the next instruction and wasnt good

entered this

:/opt/peragro_svn/cal3d/cal3d$ ./configure --prefix=$CAL3D

and got this


bash: ./configure: No such file or directory

any help greatly appreciated

thanks

chey

---

### Post by Hooloovooloo on 2008-01-17
Yeea, the install isn't very friendly yet. :D
I would get on the IRC channel and ask around. I don't know what the problem is, but i'm sure someone do.

---

### Post by mad chey on 2008-01-22
i posted asking for help on their site forums too, but all i got was someone saying that i hadnt installed something properly or not at all, tbh that wasnt very helpful because i had followed the instructions word for word as i copy and pasted everything, i think if thats their level of helpfulness i will give up on this one

---

