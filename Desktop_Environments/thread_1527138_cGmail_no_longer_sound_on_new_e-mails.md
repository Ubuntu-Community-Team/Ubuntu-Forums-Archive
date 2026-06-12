---
title: "cGmail: no longer sound on new e-mails"
date: 2010-07-08
forum: Desktop Environments
---

### Post by piko7 on 2010-07-08
Option to play sound is checked (same option in gconf-editor is checked too). But there is **no sound on new emails**.

Default notification file (notify.wav) is playing OK with other software.

I even try to edit source code (python) of cGmail to disable check of option in gconf-editor. But still no sound.

Maybe it is some kind of problem with python's libs?
Any idea?


Terminal:

```
$ /usr/bin/cgmailservice

** (cgmailservice:10962): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (cgmailservice:10962): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (cgmailservice:10962): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
No pop3id file. Creating default...
...done

```

cGmail 0.6.1
Ubuntu 10.04 64bit

---

### Post by piko7 on 2010-07-09
The only way I could to play sound when new e-mail arrived is setup cGmail to run script like this:

```

#!/bin/bash
mplayer ~/notify.wav

```

---

