---
title: "Writing a custom xsession in Ubuntu that logs out on process end"
date: 2010-08-31
forum: Desktop Environments
---

### Post by peeta123456 on 2010-08-31
Hello,

Im trying to create a custom xsession on Ubuntu 10.04 that will launch nxclient and logout automatically when it closes.

This is what I have so far

```
#!/bin/sh
/usr/NX/bin/nxclient &
exec xterm
```

How would I go about altering this script to logout when nxclient closes? To further complicate things, nxclient spawns a separate process (nxssh) when it negotiates a connection and closes itself.

Is it possible for a script to listen for a child process to close and then execute some commands (in this case a logout)?

Apologies if I haven't explained it very well but I'm new to linux scripting.

Thanks for reading,

Cheers,
Pete

---

