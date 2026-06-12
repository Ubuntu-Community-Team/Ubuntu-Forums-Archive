---
title: "no root login at grub startup screen"
date: 2005-05-25
forum: Desktop Environments
---

### Post by laughingbuddha on 2005-05-25
hello friends. at the grub/startup screen, i can't login as root. when i try, nothing happens--it's as if i entered the wrong password, but i'm not. i tried to enable what i thought was the setting that controlled root login at startup, but despite enabling this option, i still can't login as root from the grub screen. any ideas? anything i should check or look into? thanks guys.

---

### Post by Masato on 2005-05-25
A few things:

1.) Due to security risks, the root is disabled in Ubuntu from logging in, or anything. 
2.) Check your /etc/passwd file. Use vi in the terminal. ```
sudo vi /etc/passwd
```

---

### Post by netrattler on 2005-05-25
If you really want to root access at login the ubuntuguide tells you how to do this, although I don't recommend it. Here is the link.

[http://ubuntuguide.org/4.10/index.html#allowrootlogingnome](http://ubuntuguide.org/4.10/index.html#allowrootlogingnome)

Joe

---

