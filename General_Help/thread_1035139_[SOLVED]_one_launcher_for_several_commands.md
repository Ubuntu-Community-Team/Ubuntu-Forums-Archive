---
title: "[SOLVED] one launcher for several commands"
date: 2009-01-09
forum: General Help
---

### Post by Andreas1 on 2009-01-09
well, i am sure there is an easy way to do this: i want, for example:
an icon "go online" that starts pidgin and skype and mail-notification all at once
by the way, is it possible to also add connecting to vpn to that launcher?

---

### Post by heindsight on 2009-01-09
well you could write a script to launch all the apps you want.

eg to launch both skype and pidgin you can use the following script:
```

#!/bin/sh

skype &
pidgin &

```

save it and give yourself permission to execute it, then create a panel launcher for it.

---

### Post by Andreas1 on 2009-01-09
would that be a "filename.sh" file?

---

### Post by heindsight on 2009-01-09
> **Andreas1 said:**
> would that be a "filename.sh" file?

yes

---

