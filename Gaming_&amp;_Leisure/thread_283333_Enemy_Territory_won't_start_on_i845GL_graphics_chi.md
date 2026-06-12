---
title: "Enemy Territory won't start on i845GL graphics chipset in dapper drake"
date: 2006-10-24
forum: Gaming &amp; Leisure
---

### Post by doublepow on 2006-10-24
Hello,

 I have installed Enemy Territory version 2.60 on an Ubuntu Dapper Drake installation. My graphics chipset is Intel 845GL. When I type et from the command line to start Enemy Territory, the screen goes blank first, then a blank new window opens up and after a few seconds my mouse pointer disappears eventually requiring me to restart the X server to get back things to normal.

How do I get Enemy Territory to work?

Thanks.

---

### Post by Somniis on 2006-10-24
Have you ran ET on that chipset before?

I don't know if that chipset supports direct rendering, but type this into the terminal and see:
```
glxinfo | grep direct
```

If it says "direct rendering: yes" then it is obviously something else that causes it to crash.  :???:  Possibly the drivers?

---

### Post by chavo on 2006-10-24
It'll run on there but it's gonna be way to slow to play. I've had it running on Linux and Windows but it's just not playable. The system is a Dell Inspiron 2Ghz celeron and 385Mb RAM. I know it's kind of weak, but I'm pretty sure the card is the weakest link here.

---

### Post by doublepow on 2006-10-24
Somniis yes glxinfo shows "Direct Rendering: Yes". I haven't run ET on Linux before, I'm trying it for the first time. I play ET on Windows and it runs fine with minimum Video settings. 

Chavo oops that's unfortunate. I was hoping to not have to boot into Windows at all but seems I will still have to.

Thanks for the replies, I appreciate it

---

