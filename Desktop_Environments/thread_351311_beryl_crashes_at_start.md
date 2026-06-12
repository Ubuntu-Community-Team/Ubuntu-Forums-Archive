---
title: "beryl crashes at start"
date: 2007-02-01
forum: Desktop Environments
---

### Post by AxietY on 2007-02-01
hi, I'm using beryl with aiglx with ubuntu 6.10, i have a Compaq nx9000 laptop.
when i rin beryl with "beryl-manager" command in the terminal, my 'X' crashes and i need to restart it :<,
i managed too see something about tests, it passed them all except one:
".. non power of two textures.. : failed "
can any1 help me with this please

---

### Post by allwin on 2007-02-01
You need a better video card driver.  In my case, I used a program called ENVY (Google for that) to install the latest nVidia drivers (if you have nvidia that is).  The nv legacy driver just doesn't cut it, neither does the "nv" open source one, gotta be the proprietary driver from nVidia.  Then for ATI, the open source "ATI" driver worked fine for me on an old ATI card, whereas the proprietary "fglrx" one would not work.  Don't know what the situation is with Intel graphics or others.  Lots trial and error!

---

### Post by AxietY on 2007-02-02
i have a  ATI RS200/RS200M AGP Bridge [IGP 340M], and  used AIXGL is  that right ?

---

### Post by allwin on 2007-02-03
I think so.  I have an older ATI card, which works with the open source "ATI" driver.  I understand the fglrx driver doesn't work with Beryl unless you use XGL.

---

