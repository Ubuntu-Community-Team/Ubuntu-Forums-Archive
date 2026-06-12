---
title: "iPod detection problem"
date: 2006-06-28
forum: Desktop Environments
---

### Post by minorthreat on 2006-06-28
When I plug in my iPod, if it is the first time since boot, it is detected fine and it mounts and works as supposed to.  However, after I unmount, it is no longer detected when I plug it in.  This is the output I get from dmesg: ```
[17181857.164000] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[17181857.436000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
```

It's pretty annoying to have to reboot every time I want to add music.  Where else can I look to see where the problem might be and find a solution?

---

### Post by Joeb on 2006-06-30
Not a perfect solution, but instead of rebooting try issuing the command sudo rmmod ieee1394  from the command line and then issue sudo insmod ieee1394.  After that plug your ipod back in.  If the rmmod complains about other modules depending on ieee1394 then remove and insert them, too.

---

