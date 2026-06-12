---
title: "AWN on Startup"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by SRX on 2007-10-02
is there anyway to make AWN startup 30 seconds after boot ?

because AWN always starts up before Compiz Fusion and I get a black rectangle where AWN should be 

thanks 

sr

---

### Post by hyperair on 2007-10-03
Create a file somewhere in your home directory.

In it, put this:
```

#!/bin/sh
sleep 30;
exec avant-window-navigator;

```

Save it, make sure the file has permission to execute. Then exchange your "avant-window-navigator" entry in Sessions.
The command must be /path/to/the/file/you/just/created

---

### Post by SRX on 2007-10-05
thanks a lot it helped and now it finally works

---

### Post by Nessa on 2007-10-06
This is very useful. Thanks too!

---

