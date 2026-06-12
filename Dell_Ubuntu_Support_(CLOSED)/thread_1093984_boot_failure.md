---
title: "boot failure"
date: 2009-03-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gourab17 on 2009-03-12
hi ..
i have both vista and ubuntu in dell xps1330 ....
sadly everything works fine for few months until there occurs a complete boot failure...i.e the grub suddenly gets deleted..
this has happened several times..and each time i had to use livecd ..backup the data and reformat .....

can anyone suggest me a remedy....and the probable reason why this is happening ..... is it a problem of ubuntu ???????? :(

---

### Post by armandh on 2009-03-12
probably not ubuntu
more likely a virus in the other partition that wipes the MBR at irregular moments.
does the failure always occur after using a windows partition?

it may be possible to use a live grub editor to redo the MBR with out a complete reload. [if that is the problem]

try just ubuntu partition for a while and if the problem does not happen try the windows partition again. if the problem happens upon booting after a windows use the problem is likely something in the windows partition wiping the MBR

---

### Post by gourab17 on 2009-03-12
thx...
a virus in windows wiping of mbr is highly possible ...because always problems start after using the windows partition.....
what is a live grub editor & how to use it......

---

### Post by sirebral on 2009-03-12
Do you allow windows to check the disk for errors?  I think that ruined one of my installs so I tried stopping that every time it ran during startup.

---

### Post by armandh on 2009-03-12
> **gourab17 said:**
> thx...
a virus in windows wiping of mbr is highly possible ...because always problems start after using the windows partition.....
what is a live grub editor & how to use it......

I know it is down loadable 
it's use is a bit over my head
but I know one can set up the boot load manually with it
and you would still have the problem next windows use.

I suggest reload windows then reload ubuntu

---

