---
title: "Help me uninstall a programme"
date: 2006-07-09
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-07-09
I installed 3d desktop with apt-get
```
apt-get install 3ddesk
```
and now i want to get rid of it , i think it's interfering with my screensaver
I uninstalled it with synaptic but when i ps ax its still there:
```
19774 ?        SNs    0:00 3ddeskd
```
how do i get rid of it?

---

### Post by simonn on 2006-07-09
```

killall 3ddeskd

```

or

```

kill -s KILL 19774

```

---

### Post by seshomaru samma on 2006-07-15
Thanks

---

