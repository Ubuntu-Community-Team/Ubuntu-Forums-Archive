---
title: "Swap question"
date: 2005-10-14
forum: Desktop Environments
---

### Post by 11hjpphty76lkjj on 2005-10-14
I know this might be a silly question.  I just installed Breezy.  And how to I make sure my swap drive is setup?  In the Places>Computer I see an unmounted partition that is the exact size of the swap drive I setup..so I was thinking maybe I didn't set it up correctly?

How do I make sure the swap is being used, and if not how to I make it use the swap.

Thanks.

Aaron

---

### Post by HermanAB on 2005-10-14
# swapon -s

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by az on 2005-10-14
You can see this in the system monitor, or you can type
free
from a terminal.

---

