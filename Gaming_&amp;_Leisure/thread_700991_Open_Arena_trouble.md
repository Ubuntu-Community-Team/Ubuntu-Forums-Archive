---
title: "Open Arena trouble"
date: 2008-02-18
forum: Gaming &amp; Leisure
---

### Post by Teddy Picker on 2008-02-18
Ok, I am trying to install Open Arena 0.7.0 but I cant figure out how. I switched to Ubuntu in October '07, so I am not entirely new to Linux. I downloaded the game, and looked through the forums to answer my problem but none really helped. do I need WINE to install it due to the .exe? or can I compile it into in Linux somehow to install? I looked but could not find a Debian installer either so if anyone knows where I could get one it would probably solve my issue. Thanks

---

### Post by aidanr on 2008-02-18
It's in the universe repo. In a terminal type:
```
sudo apt-get install openarena
```

---

### Post by DoktorSeven on 2008-02-18
But...

the Universe repo has the old (0.6.0) version, and he probably wants the latest (0.7.1).

[http://www.getdeb.net/app.php?name=openarena](http://www.getdeb.net/app.php?name=openarena) would be the best place to get a current package.  You need both the **openarena** and **openarena-data** packages to play the client; you don't need **openarena-server** unless you want to run a dedicated server.

---

### Post by aidanr on 2008-02-18
The backports repo also has 0.7.1. You can enable that through synaptic -> settings -> repositories -> updates -> check unsupported updates.

---

### Post by Teddy Picker on 2008-02-19
ok, so now that i have the **open-arena** file and **open-arena-data** do I run the debian file and it compiles the game from the data file?

never mind, got it installed. now when i play the single player it crashes most of the time. i think the patch might help this issue though, where do i install the patch to?

---

