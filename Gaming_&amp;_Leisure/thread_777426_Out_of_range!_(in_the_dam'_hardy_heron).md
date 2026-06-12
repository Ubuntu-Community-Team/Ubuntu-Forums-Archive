---
title: "Out of range! (in the dam' hardy heron)"
date: 2008-05-01
forum: Gaming &amp; Leisure
---

### Post by emshains on 2008-05-01
I loved playing games like Warsow in Gutsy and it went fine. I installed them manually without apt-get. 

Now in the dam' hardy heron I installed them through apt-get and each time I try to run them my monitor seems to cant handle the frequencie the game (s) is (are) requesting. I even tried the backuped manual installations and they didnt work neither. 

 I havent changed any hardware or the monitor so I want to know how to change the default frequencie that is given out by ,for example, Warsow ?

---

### Post by Perfect Storm on 2008-05-01
Try play around with:
```
nano ~/.warsow/basewsw/config.cfg
```
[size=1]Save: [ctrl]+[o] - Exit: [ctrl]+[x][/size]

Buttom of that file are the stuff you're looking for.
Also try set **set gl_ext_texture_non_power_of_two "1"** to 0

By the way get the latest instead, 0.42 - you can install it manually or by deb packages from getDeb.

---

### Post by emshains on 2008-05-02
> **Artificial Intelligence said:**
> Try play around with:
```
nano ~/.warsow/basewsw/config.cfg
```
[size=1]Save: [ctrl]+[o] - Exit: [ctrl]+[x][/size]

Buttom of that file are the stuff you're looking for.
Also try set **set gl_ext_texture_non_power_of_two "1"** to 0

By the way get the latest instead, 0.42 - you can install it manually or by deb packages from getDeb.

Thanks!

I will try that, when I have some free time.

---

### Post by emshains on 2008-05-04
Cool, I dont have a config file there. (sarcasm) 


Now what do I do?

---

### Post by Perfect Storm on 2008-05-04
Here's mine. It should had made one by default...though.
Note, you might want to make changes as it set up for my computer.

---

### Post by emshains on 2008-05-11
> **Artificial Intelligence said:**
> Here's mine. It should had made one by default...though.
Note, you might want to make changes as it set up for my computer.

Thanks.

---

