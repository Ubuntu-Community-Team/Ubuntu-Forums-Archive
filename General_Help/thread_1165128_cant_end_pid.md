---
title: "cant end pid"
date: 2009-05-20
forum: General Help
---

### Post by max_power on 2009-05-20
maybe im doing this wrong, but im trying to stop conky by ending the pid but i get the error "stop: Unknown job:xxxx"

Conky tells me that conky is running on PID 6961

so i do:
```
sudo stop 6961
```

and the message i get is:
```
stop: Unknown job:6961
```

Any help?

thanks

---

### Post by geirha on 2009-05-20
You use kill to tell a process to terminate.
```

kill 6961
# You can also kill by process name
killall conky

```

---

### Post by max_power on 2009-05-20
awesome thanks.. i hadnt used kill in a long time and i guess i confused it with end.. thanks@!

---

