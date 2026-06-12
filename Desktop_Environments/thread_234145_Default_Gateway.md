---
title: "Default Gateway"
date: 2006-08-11
forum: Desktop Environments
---

### Post by macca87 on 2006-08-11
Hey everyone,
Just a quick question. I like to make my own scripts for things so that they only run when i need them to instead of using the startup ones. I need to know the command to set the default gateway by the command line.

eg. I have a script which turns on my wireless card, coonects using ifconfig, and the connection works, however i can't access the internet through firefox, etc... since the default gateway is not being set.

Can anyone help me with the command?
Thanks in advance

---

### Post by aggyb on 2006-08-15
Am not at a Linux PC right now so I can't test this but you could try:
```
sudo route add default gw <ADDRESS>
```

If this doesn't work it's worth checking whether you can ping the gateway.

Hope that helps

AggyB

---

### Post by fragos on 2006-08-15
DCHP sets default gateway unless you have a static IP for Internet access.  In that case you will need to set it yourself.

---

