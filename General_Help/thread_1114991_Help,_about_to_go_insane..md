---
title: "Help, about to go insane."
date: 2009-04-03
forum: General Help
---

### Post by netside on 2009-04-03
I'm trying to install AIM on Ubuntu, and I'm following the directions on AOL's site to the "T".  However, I'm getting nowhere, except getting the archive to unzip.  Simply put, I can't get it to run, and am very new to the linux world.  Can somebody please help me?  I attached two images of the terminal window, so that you all can see what I'm doing wrong.  I did exactly what the site says, but when I go to run aim through the terminal, it always hits me with various messages (file not found, etc).  What am I doing wrong?  Thanks guys!

---

### Post by wicky_ts on 2009-04-03
I am not familiar with AIM. what I can tell is you cant do anything outside your home directory as the normal user. so try the instruction in AIM starting from 

sudo ........

then terminal will ask you for your password. give your password. 

try this work

---

### Post by ptn107 on 2009-04-03
AIM -> Pidgin

---

### Post by albinootje on 2009-04-03
> **netside said:**
> I'm trying to install AIM on Ubuntu
Pidgin supports AIM, and is installed by default on Ubuntu. 

For your specific problem, try the following :
```

sudo apt-get install libgtk1.2

```

---

