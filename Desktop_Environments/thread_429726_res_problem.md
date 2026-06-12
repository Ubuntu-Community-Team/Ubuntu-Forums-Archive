---
title: "res problem"
date: 2007-05-01
forum: Desktop Environments
---

### Post by NerdyRukia on 2007-05-01
Hi!

I have ubuntu 6.06 LTS and I have this weird prob...

It loads normally but when it's time to login the monitor hibernates. 
I can still put on the username and password and I ear it entering the desktop... but it's kind of hard working there without seeing anything....

I was told it's a res prob... but I can't seem to access the res configuration in recovery mode...I'm just too noob ... =X

anyway... how should I do it? and do you think it can be some other thing?:confused: 

thanks in advance =S

---

### Post by taurus on 2007-05-01
From recovery mode, run

```
dpkg-reconfigure -phigh xserver-xorg
```

---

