---
title: "X rdesktop client"
date: 2011-02-18
forum: Desktop Environments
---

### Post by cccc on 2011-02-18
Hello

I need a really simple X rdesktop client to run under xfce desktop.
Is it any other solution than remmina or tsclient?

---

### Post by cccc on 2011-03-05
Installing **zenity** package and this script:```

#!/bin/bash

address=$(zenity --title="New RDP Connection" --entry --text="RDP Server IP address:")

rdesktop $address
```solved my problem.

---

### Post by hugmenot on 2011-04-01
> **cccc said:**
> Installing **zenity** package and this script:```

#!/bin/bash

address=$(zenity --title="New RDP Connection" --entry --text="RDP Server IP address:")

rdesktop $address
```solved my problem.

Use xfreerdp. It&#8217;s a fork of the stalled rdesktop.

```
xfreerdp -d XXX -p "xxxxx" -a 32 -x 0x80 -z --plugin cliprdr -g 1280x850 host
```

---

