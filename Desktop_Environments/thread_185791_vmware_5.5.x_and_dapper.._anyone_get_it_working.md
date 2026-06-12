---
title: "vmware 5.5.x and dapper.. anyone get it working?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by binskipy2u on 2006-06-01
anyone get vmware 5.5.x working in any previous rc's or betas or this new one (i know its early) of 6.06?
just wondering, i use pclinuxos, and it takes altering of 3 install files in the "hopes" that vmware works.. if it does w/no fancy smancy googling of the net looking for "hacks" then ill go back to ubuntu.. but all it all from the contents of the new release and screeenshots it looks FRIGGIN AWESOME

thanks for any help

---

### Post by philipgm on 2006-06-01
I don't know if this helps, but I just installed VMWare Server on 6.06 and then Windows XP and everything seems to work fine.

There's a HOWTO for that here 

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

HTH  

Phil

---

### Post by Akita on 2006-06-01
It's been working fine for me since Flight 4 or so when I last installed it. No problems whatsoever.

---

### Post by denjin on 2006-06-01
Yeah I've been using it for -ages- under Dapper.  Just have to re-run the config script sometimes if your kernel gets updated.

Check out that howto posted a few up.  You'll need the kernel headers, gcc, make, etc.

---

### Post by joske on 2006-06-01
I had to copy /lib/libgcc_s.so.1 to the vmware lib dir to make it work (talking about vmware workstation - not player - here). Found it on the vmware forums.

---

