---
title: "Can I stop the desktop freezing when I am asked for my password for admin tasks?"
date: 2010-07-06
forum: Desktop Environments
---

### Post by njsharp on 2010-07-06
I often want to have mythtv running on one display while I continue with work on the main display, as I CAN chew gum and walk at the same time.

When the task is administrative, such as running update manager, I am asked for my password so Ubuntu (10.04 amd64) can authenticate me as an administrator.  Good, but I THINK I would like it NOT to freeze the desktop, including the mythtv, while it does so.  Is there a good reason NOT to want that?

If not, can it be done (avoid freeze when authenticating) and if so, how?

I have not found help elsewhere - sorry if I missed it!

---

### Post by stinkeye on 2010-07-07
For update-manager you could run in terminal
```
sudo apt-get update && sudo apt-get upgrade
```
You would have to search for terminal commands for other administrative tasks.

---

