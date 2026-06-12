---
title: "aircrack problems"
date: 2008-12-26
forum: General Help
---

### Post by xGutsAndGloryx on 2008-12-26
I just downloaded aircrack. I can't get it to work. I looked up on some forums and found out i might need to patch my madwifi driver. how do i do that?

---

### Post by pytheas22 on 2008-12-26
madwifi drivers are only for certain wireless cards, and in most cases they shouldn't actually require patching on modern versions of Ubuntu.  You may have a card that uses an entirely different driver that may or may not require patching.  If you could please open up a terminal, run the following commands and post the output, I'll try to point you in the right direction:
```

lspci -nn
lsusb
lshw -C Network
uname -rm
```

---

