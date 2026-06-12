---
title: "xfce4-terminal: text colours lost when command is run from a script"
date: 2014-08-23
forum: Desktop Environments
---

### Post by Kirkx on 2014-08-23
When I execute the following command directly from the terminal the kernel version number appears in red:

```
dpkg --list linux-* | awk '/^ii/{ print $2 }' | grep -e [0-9]
```

When the same command is executed from a script the kernel version number appears in the default green:

[http://i.imgur.com/EPD10oI.png](http://i.imgur.com/EPD10oI.png)

Is there any way to get that red colour back?

Here is the command used to open the terminal from Main Menu entry (or Alt+F2):

```

xfce4-terminal --geometry=78x20 -T "Kernel Information" -e "bash -c /usr/scripts/kernel-info.sh;bash"

```

And here is the script "kernel-info.sh":

```

#!/bin/bash

dpkg --list linux-* | awk '/^ii/{ print $2 }' | grep -e [0-9]

# Script End

```

--------
Xubuntu 14.04.1, xfce4-terminal 0.6.3

---

### Post by steeldriver on 2014-08-23
Try

```

dpkg --list linux-* | awk '/^ii/{ print $2 }' | grep **--color=always** -e [0-9]

```

---

### Post by Kirkx on 2014-08-26
Thanks, now it works like a charm. Sorry for late reply. Marked as Solved.

---

