---
title: "Tmp ?"
date: 2005-01-21
forum: Desktop Environments
---

### Post by ThePainter on 2005-01-21
Hi,
There is a folder called /tmp apparently this is a temperary file holder.
Can I safely empty this ?
In Mandrake there is an option to empty the tmp folder on logout but I cant find one here, is there one ?

---

### Post by ecor6633 on 2005-05-07
It seems that a crontab script does it for you automatically and that's a problem for me.
I'm developping a perl application and wanted to use a subdirectory in /tmp for my apache cookies but this subdirectory always disappear.

So I suppose you don't need to worry, your tmp dir should be empty but if anybody could explain us where is this crontab script and what it does exactly.

If anybody knows how to keep a subdirectory in /tmp that would be very helpfull

---

### Post by ThePainter on 2005-05-07
Hi,
Thanks for replying, I hope you get your answer and I hope your post helps someone but myself I moved over to Mepis over a month ago and it lists tmp being emptied on the boot up scripting.
Good luck on your quest.
Take care.

---

### Post by mrt on 2005-07-21
/etc/init.d/bootclean.sh has code that cleans out /tmp - should be a good place to start

---

### Post by szundi on 2005-08-23
You should put a .clean file in the tmp dir if i'm right

---

