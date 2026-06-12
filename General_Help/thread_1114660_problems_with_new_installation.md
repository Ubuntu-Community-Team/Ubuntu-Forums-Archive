---
title: "problems with new installation"
date: 2009-04-03
forum: General Help
---

### Post by tkearn5000 on 2009-04-03
I am new to linux, and recently installed ubuntu. The installation went fine. After I restarted my computer, everything was working well, until I signed into ubuntu. After signing in, the screen went tan, then black. It stayed black for about ten minutes. I restarted my computer, and now when I sign in, the screen turns tan, and stays that way. Does anybody know why this is happening?
I installed as a dual boot, and windows still works fine. I just can't seem to get ubuntu to go past the login screen.

---

### Post by Dejai on 2009-04-03
When you come to the login screen can you get to a terminal?: To do so type the following command. CTRL+ALT + F1 (this also works with F2-3,4,5,6) if you can log in there, that is a good start. But I would probably suggest something went wrong in your installation and you should try and repair it via the CD you used to install the distro.

---

### Post by kpkeerthi on 2009-04-03
Try removing compiz.

1. From GRUB boot menu, boot into "Recovery Mode"
2. At the command prompt, enter the below commands:
```

sudo apt-get remove compiz compiz-core

```
3. Reboot
```

sudo shutdown -r now

```
4. Boot into normal mode this time.

---

### Post by tkearn5000 on 2009-04-03
Thanks,
I already got that info off of another post. It worked out though.
Thanks for the reply.
-TK

---

