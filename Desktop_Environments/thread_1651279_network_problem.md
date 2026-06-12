---
title: "network problem"
date: 2010-12-22
forum: Desktop Environments
---

### Post by emilemma on 2010-12-22
just installed 10.10 and all went well during install, but as soon as i tried to do anything else, ubu won't connect to the network. i have dual boot with win 7 pro and there is no problem there. as a matter of fact, i am here on forum with no problem. am i doing something wrong or what??

thanks much...

---

### Post by NorlanBustillo on 2010-12-22
try in failsafe mode or update the packages (in generic mode). there you can maybe fix the issue

---

### Post by pytheas22 on 2010-12-22
If the suggestion above doesn't help, please post the output of these commands so we can get a better idea of what might be wrong:
```

lshw -C Network
lspci -nn
lsusb
uname -a
ifconfig
grep NetworkManager /var/log/syslog
```

Also, are you trying to connecting via ethernet or wirelessly?

---

### Post by emilemma on 2010-12-22
not familiar with failsafemode...  problem seems to have gone away for now..   will keep watch & get back if more problems

thanks very much  connecting via wired connection  eth0  i believe..

p.s  linux newbie..

---

