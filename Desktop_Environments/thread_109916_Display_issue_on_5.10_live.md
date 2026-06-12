---
title: "Display issue on 5.10 live"
date: 2005-12-29
forum: Desktop Environments
---

### Post by alexport on 2005-12-29
Hello people.
I tried to boot from my cd and faced the following problem.
Although the installation procedure run ok, when it finished and logged in, there where vertical RGB lines on my screen, but the sound of the initiation was heard ok... :(  I have a brand new LG 1950SQ LCD monitor with Nvidia's 6600GT VGA...
Has anybody had this problem??

---

### Post by aysiu on 2005-12-30
Installation or live?

If it's live (as your thread title seems to indicate), try ```
boot vga=791
``` instead of just pressing Enter.

If it's installation (as your post seems to indicate), try Control-Alt-F1 ```
sudo dpkg-reconfigure xserver-xorg
```

---

