---
title: "Starting gnome-terminal with command running in one tab"
date: 2010-03-10
forum: Desktop Environments
---

### Post by misha680 on 2010-03-10
I have the following in ~/.gnome2/session:
```

9,Program=gnome-terminal
9,CurrentDirectory=/home/misha
9,CloneCommand=gnome-terminal --sm-config-prefix /gnome-terminal-M5lHVS/ -x sh -c "/home/misha/bin/check-up"
9,RestartCommand=gnome-terminal --sm-config-prefix /gnome-terminal-M5lHVS/ --sm-client-id 117f000101000126688793600000078420011 --screen 0 --window-with-profile-internal-id=Default --show-menubar --role=gnome-terminal-9859--1293676128-1266887936 --active --geometry 237x61+0+30 --title misha@misha-d630:\\ ~ --working-directory /home/misha --zoom 1 -x sh -c "/home/misha/bin/check-up"

```

where /home/misha/bin/check-up is
```

#!/bin/bash
while [ 1 ]; do
   ssh -C venus.hnl.bcm.edu
   sleep 10
done 

```

both the CloneCommand and RestartCommand work perfectly when I execute them (for example from Alt-F2). A terminal starts where the _first_ tab runs my command and others run a shell.

However, at startup, I instead get a terminal where the first _and second_ tabs seem to run my command.

Any help much appreciated!

Thank you
Misha

---

