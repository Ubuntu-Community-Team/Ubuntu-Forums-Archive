---
title: "I can't Log in due to refresh rate"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Justin Holt on 2006-09-02
WELL...AS YOU CAN SEE FROM THE TITLE, I CAN'T LOG IN, HOWEVER I AM POSTING FROM LINKS SO I CAN FIND AN ANSWER. MY problem is that when i go to log in, my monitor startes telling that the refresh rate is too high and that i have to lower it. I know that there is a way to do it inside of gnome and such but i know that i once came upon a command to allow me to do it but i forgot that command, i think it started with sudo dpkg yada yada. I just need to lower the rate so that my monitor can work. usually when i am on my other computer the video card automatically fixes it but this is working off of on board graphics and im assumming it is smart enough to do that...any help would be appreciated

---

### Post by taurus on 2006-09-02
You can reconfigure your X (and monitor) again with, from a terminal

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Justin Holt on 2006-09-02
thank you very much...i see colors now.

---

### Post by taurus on 2006-09-02
> **Justin Holt said:**
> thank you very much...i see colors now.
So everything is good now!!!

---

