---
title: "Running 'source' from a script"
date: 2009-02-07
forum: General Help
---

### Post by FokkerCharlie on 2009-02-07
Hi All

I have saved my joystick calibration to a file, which I can retrieve by using this command from the terminal:

```
source ~/ .. /logitechwm.cal
```

However, putting this in a script (called joyrecall.sh) like so:
```

#!/bin/sh

source /home/charlie/technicals/scripts/logitechwm.cal
```

Doesn't work out, returning this error:

```
$ sh joycalrecall.sh
joycalrecall.sh: 3: source: not found
```

So what's going on here?  I'd like it in a script, so I can run it at each login (via sessions) or from a menu or panel item.

Thanks in advance!

Charlie

---

### Post by andrewc6l on 2009-02-07
source is a builtin only in /bin/bash and not in /bin/sh (which is acutally a link to /bin/dash). Try changing the first line of your script to:

#!/bin/bash

---

### Post by FokkerCharlie on 2009-02-07
Ah-ha!

Making your change, and running the script as "bash <script name>" fixed it a treat.

Thanks!

I'm not sure I understand the sh/bash issue, but there you go.  It works.

Cheerio
Charlie

---

### Post by geirha on 2009-02-07
If you want it to work in both shell, use '.', which both shells accept.

```

. logitechwm.cal      # both /bin/sh and /bin/bash

source logitechwm.cal # only /bin/bash

```

---

### Post by andrewc6l on 2009-02-07
I was just about to say the same thing :-) Here's a page that describes the differences between bash and dash:

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

