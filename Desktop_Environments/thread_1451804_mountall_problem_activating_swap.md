---
title: "mountall: problem activating swap"
date: 2010-04-11
forum: Desktop Environments
---

### Post by covertcj on 2010-04-11
Hi,

Earlier today I installed Ubuntu 9.10 using the 12~ MB minimal cd, and I have run into an issue. It happens every time I boot, including the first time I ever did after installation. The console outputs several lines and then continues to the login prompt as usual. The output is as follows

```
swapon: /dev/sda5: read swap header failed: invalid argument
mountall: swapon /dev/sda5 [873] terminated with status 255
mountall: problem activating swap /dev/sda5
```My swap is indeed on /dev/sda5, and I really don't know where to go with this. The system seems to work fine (I'm just assuming I don't actually have a swap active).

Any help with this issue would be *greatly* appreciated. I have installed an Ubuntu 9.10 minimal install before and have never run into this issue.

Thanks,
Chris

---

