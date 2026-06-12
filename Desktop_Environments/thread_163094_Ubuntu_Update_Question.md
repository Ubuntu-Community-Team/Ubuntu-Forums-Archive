---
title: "Ubuntu Update Question"
date: 2006-04-20
forum: Desktop Environments
---

### Post by Dambrosio on 2006-04-20
I was wondering if there is a way to update ubuntu through command line(I dont think thats the right term)? Because whenever I try and update using ubuntu's update program it never works, it just closes after I hit apply. Is this a problem that I need to fix or would it be ok to just go around it and use the terminal.
Thanks,
Dan

---

### Post by openmind on 2006-04-20
```
sudo apt-get update
```

Don't know why your update isn't working.

---

### Post by ronb on 2006-04-20
I have the same problem with Update Manager, so I only use it to notify me that there's an update available.

I use **System > Administration > Synaptic Packager Manager **for updates.  Works great.

---

### Post by towsonu2003 on 2006-04-20
```
sudo apt-get update
sudo apt-get -s upgrade #optional, to see what packages it will upgrade etc /s means simulate
sudo apt-get upgrade
```

---

### Post by Dambrosio on 2006-04-20
Thanks.

---

