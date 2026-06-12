---
title: "Desktop effects OFF switch please!"
date: 2007-11-21
forum: Desktop Effects &amp; Customization
---

### Post by mansell on 2007-11-21
Am newbie and installed Ubuntu 'gutsy' yesterday, and was fine until I activated Desktop Effects today; then after reboot screen display is stripes, wiggly and multiple. I need command to disable Desktop effects via the recovery prompt- not in graphics mode( since I can't see anything).
Thanks

---

### Post by mrmiserable on 2007-11-21
killall compiz

i think that will work

---

### Post by mansell on 2007-11-21
This did not work. command replied: "no process filled"
So this leaves only one more option that I changed during that session; I changed the monitor from "generic vesa..." to its proper brand name "BenQ FP71E". Now I need this command to change it back to generic, please. By the way, is there a quick list of often used commands for download?

---

### Post by RSingh on 2007-11-21
try reseting your xorg.conf file:

use this command in terminal and reboot.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by smartboyathome on 2007-11-21
You don't need to type the terminal, since you are already root in the recovery prompt. Just leave that part out.

---

### Post by markp1989 on 2007-11-21
> **mrmiserable said:**
> killall compiz

i think that will work

i think it is compiz.real you need to kill, but i have never tried it my self

---

### Post by mansell on 2007-11-21
command: sudo dpkg-reconfigure -phigh xserver-xorg  did the trick.
I committed this error years ago in Windows and resolved it by same DOS method.
It's just to know the proper command. My learning curve begins...
Thank you

---

### Post by amadeus266 on 2007-11-21
Maybe this will help [http://ubuntuforums.org/showthread.php?p=3816218#post3816218](http://ubuntuforums.org/showthread.php?p=3816218#post3816218)

---

