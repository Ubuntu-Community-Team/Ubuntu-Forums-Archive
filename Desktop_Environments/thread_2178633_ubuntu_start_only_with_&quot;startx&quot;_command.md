---
title: "ubuntu start only with &quot;startx&quot; command"
date: 2013-10-04
forum: Desktop Environments
---

### Post by peppe3 on 2013-10-04
Hi, I've just installd ubuntu 12.04 on my hp laptop with ati radeon hd 4560, but when I start it, I see only a black screen with "battery status" words. After entering in terminal, the only way to use desktop is by startx command. I can I solve the problem??

Thanks.

---

### Post by ibjsb4 on 2013-10-04
My guess would be the display manager (lightdm) has malfunction.  Try something simple.

```
sudo dpkg-reconfigure lightdm && sudo reboot
```

---

### Post by peppe3 on 2013-10-04
ok thanks,I've choosen lightdm instead of gmd and  now it works.

---

### Post by ibjsb4 on 2013-10-04
Probably something in your gdm configuration file is not right, but nothing wrong with using lightdm.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=configure+gdm&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=configure+gdm&sa=Search&cof=FORID:9)

---

