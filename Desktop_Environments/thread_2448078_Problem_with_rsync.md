---
title: "Problem with rsync"
date: 2020-08-01
forum: Desktop Environments
---

### Post by richardi99 on 2020-08-01
Hi
I am trying to use Rsync and getting an error.  Can anyone please help?

[I]rsync --progress -avz -e ssh user@x.x.x.x:/sourcefolder/* /destinationfolder
[/I]
Yields:
[I]bash: rsync: command not found
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: error in rsync protocol data stream (code 12) at io.c(235) [Receiver=3.1.3]
[/I]
Rsync is installed and current.  Remove and local folders exist.  Remote user exists.

Please help!
Thanks

Ubuntu 20.04

---

### Post by richardi99 on 2020-08-01
Solved it!  Rsync needed to be installed on the remote server too.

---

