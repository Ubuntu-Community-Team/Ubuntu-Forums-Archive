---
title: "cario dock goes to right side of screen"
date: 2010-07-01
forum: Desktop Environments
---

### Post by nacho32 on 2010-07-01
I installed the Cario dock and love it but when I start my laptop it goes to the right side then I configure it to go more left and it fixes it but when i reboot it way to the left the default center setting does not keep it centered any one else have this problem ? 10.04 32 bit

---

### Post by nacho32 on 2010-07-01
anyone?

---

### Post by fabounet on 2010-07-02
didn't you put an offset that would translate the dock on the side ?

a solution would be to start it after the Window Manager, with something like :
```
sleep 10 && cairo-dock -o
```

---

### Post by nacho32 on 2010-07-03
i have the dock centered by default settings if thats what your asking but still after a reeboot it goes to the right side of the screen

---

### Post by fabounet on 2010-07-03
did you try with the sleep ?
maybe 10s is not enough

---

### Post by nacho32 on 2010-07-04
I put that command in the start in cario dock and it just fails to start so i put the default back in cairo-dock -o

---

