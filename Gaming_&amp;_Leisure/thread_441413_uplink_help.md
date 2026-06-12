---
title: "uplink help"
date: 2007-05-12
forum: Gaming &amp; Leisure
---

### Post by randomperson on 2007-05-12
I have a fresh install of Ubuntu feisty fawn and have tried to install unlink on it.  I have the downloaded version 1.3 and have unpacked it ok.  when I try to run it graphically in terminal the terminal flashes up for a fraction of a second then dispersers again, if I choose run then the box dispersers and nothing happens.  If I try to run it by typing in the terminal it comes up with the error ./lib/uplink.bin.x86: ./lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
I have looked on the package manager and it doesn't even have gcc 4.2 on there and libstdc++.so.6 is a file that comes as a basic install.  I have gcc4.1 installed because it is part of the basic install.

---

### Post by NPALeech on 2007-05-22
I had the same problem. After checking the Uplink forums I found this suggestion:

"Try renaming or deleting the libgcc_s.so.1 file in the uplink/lib directory." 

Works great for me.

---

### Post by randomperson on 2007-05-24
Thank you for this, I did look at the uplink website but couldn't find anything

---

