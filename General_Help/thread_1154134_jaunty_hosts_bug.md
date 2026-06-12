---
title: "jaunty hosts bug?"
date: 2009-05-09
forum: General Help
---

### Post by tenmilez on 2009-05-09
I've installed both the desktop and server version of 9.04 and when I look at my /etc/hosts file it says ```
127.0.0.1	localhost
127.0.1.1	morgan-desktop
``` It's been a while, but I don't remember there ever being a significance to the number 127.0.1.1, especially because it doesn't work. I have to change that if I want my Glassfish server to work.

---

### Post by IllegalCharacter on 2009-05-09
Change 127.0.1.1 to 127.0.0.1, restart and see if that fixes it.

---

### Post by tenmilez on 2009-05-09
Oh it does, I don't even think I needed to restart, but it was like this after a fresh install and it seems like something that should be fixed, if it is actually broken.

---

