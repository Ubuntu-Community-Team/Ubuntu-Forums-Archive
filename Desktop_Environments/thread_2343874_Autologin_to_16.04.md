---
title: "Autologin to 16.04"
date: 2016-11-20
forum: Desktop Environments
---

### Post by kjetil-fleten on 2016-11-20
Hello,

I have a remote 16.04 that I can access with ssh. I would like to enable autologin for a user on this machine.

I have tried to modify /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf, so it now looks like this:

```
[Seat:*]
greeter-session=unity-greeter
autologin=user1
```

I have also created a file in /etc/lightdm/lightdm.conf.d/50-myconfig.conf, that looks like this:

```
[SeatDefaults]
autologin-user=user1
```


Still, no autologin happens after reboot. 
Any idéas what might be wrong ?

---

