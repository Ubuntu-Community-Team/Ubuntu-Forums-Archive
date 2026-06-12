---
title: "Issues with Dosbox running Daggerfall, dosbox crashes"
date: 2009-07-26
forum: Gaming &amp; Leisure
---

### Post by Nisstyre56 on 2009-07-26
Hello, I followed all of the general instructions for getting the game Daggerfall to run under Dosbox. I mounted the C: drive, mounted the D: drive to get it to think it was using a CD, etc.. basically all of Bethesda's instructions from here [http://static.bethsoft.com/downloads/games/daggerfall_legal_and_installation.pdf](http://static.bethsoft.com/downloads/games/daggerfall_legal_and_installation.pdf) except Ubuntu specific. When I finally type install, it goes to the install screen, but then Dosbox suddenly disappears, and I have to start it up again, and I get the same problem each time.

If it helps, I get this error from the terminal after this happens.


```

DOSBox version 0.72
Copyright 2002-2007 DOSBox Team, published under GNU GPL.
---
CONFIG: Using default settings. Create a configfile to change them
ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
MIDI:Opened device:oss
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  139 (MIT-SHM)
  Minor opcode of failed request:  3 (X_ShmPutImage)
  Value in failed request:  0xe
  Serial number of failed request:  4923
  Current serial number in output stream:  4924
name@name:~$ 


```

---

### Post by CharmyBee on 2009-07-26
Try upgrading to 0.73.

---

### Post by kostkon on 2009-07-26
If you are using 9.04, you can get it from [*getdeb.net*]("http://www.getdeb.net/app/Dosbox").

---

### Post by Nisstyre56 on 2009-07-26
Thanks, that seems to have fixed it. I guess the version I installed with synaptic was an older version. Oh well, it's fixed now.

---

