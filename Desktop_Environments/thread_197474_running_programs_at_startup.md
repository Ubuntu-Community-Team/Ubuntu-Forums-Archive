---
title: "running programs at startup"
date: 2006-06-15
forum: Desktop Environments
---

### Post by wpshooter on 2006-06-15
If I wanted to start the folding at home program by placing it in the startup section under sessions, can I just browse to the folding command  and click on it or do I have to give the entire command just like I would at the terminal including ./folding start ?   I would like to do this instead of running folding at home as a service.

And if I started this program this way, would I need to manually stop the program each time before shutting down the system ?

Thanks.

---

### Post by mlind on 2006-06-15
There's a HOWTO for this [http://www.ubuntuforums.org/showthread.php?t=101817](http://www.ubuntuforums.org/showthread.php?t=101817)

I suggest you put folding at home to run on a daemon mode.
This requires making a init script for the process which handles startup and
shutdown automatically.

Example skeleton for the script is located on /etc/init.d/skeleton
If you need help on this, I'll assist.

---

