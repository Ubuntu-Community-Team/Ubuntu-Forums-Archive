---
title: "Firefox Problems"
date: 2005-05-24
forum: Desktop Environments
---

### Post by Pitbull11188 on 2005-05-24
Sometimes when I'm browsing Firefox has an error and force quits or unexpectedly exits. Upon reopening the application it forces me to create a new profile because the other processes from firefox are still running despite the gui being exited. Could anyone tell me how to kill the processes as "xkill" doesn't work when used on the profile window. Thanks.

---

### Post by Mez on 2005-05-24
from a command

sudo killall -9 firefox-bin
sudo killall -9 firefox

---

