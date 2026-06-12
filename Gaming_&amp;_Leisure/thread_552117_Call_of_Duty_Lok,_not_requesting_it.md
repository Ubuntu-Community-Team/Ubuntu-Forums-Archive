---
title: "Call of Duty Lok, not requesting it"
date: 2007-09-16
forum: Gaming &amp; Leisure
---

### Post by PoorGuy707 on 2007-09-16
ive installed CoD with the loki installer and it went fine,
but i cant get it to run

Out put from Terminal:
```

kris@kris-Ubuntu:~$ codmp
Wine(X)/Cedega not in your PATH

```

ive already edited the codmp and codsp files to put wine first but it still comes up with that error

---

### Post by reset3x on 2007-09-16
This is what worked for me... In /usr/local/bin/ I edited codsp and codmp... The first line has ```
#!/bin/sh
``` I changed it to ```
#!/bin/bash
```

After that I had no problems..

Hope this helps you out!!

Good luck!!

---

### Post by PoorGuy707 on 2007-09-16
dude thats sick,
worked like a charm,

Thanks :D:D

---

### Post by reset3x on 2007-09-16
Awesome!!! Have fun!! Great Game!!!

---

