---
title: "Run process in background between selected hours"
date: 2005-05-05
forum: Desktop Environments
---

### Post by mirtux on 2005-05-05
Hi,
   i would like to know how is possible to set up a script that is able to launch a selected program during the night, let's say from 9pm to 8am. How could i do it? Maybe using anacron?

Thanks,
MC

---

### Post by liljencrantz on 2005-05-05
[QUOTE=mirtux]Hi,
   i would like to know how is possible to set up a script that is able to launch a selected program during the night, let's say from 9pm to 8am. How could i do it? Maybe using anacron?

Thanks,
MC[/QUOTE]
 Use 'crontab -e' to start up a program at a given hour. 

If your program does not stop by itself, you kan signal it using kill or killall. 

Example crontab file:

0 21 * * * $HOME/bin/frazboogle
0 8 * * * killall frazboogle

Check out 'man 1 crontab' and 'man 5 crontab'  for more information.

---

### Post by mirtux on 2005-05-05
Thanks very much, your post has been useful!

Regards,
MC

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=mirtux]Hi,
   i would like to know how is possible to set up a script that is able to launch a selected program during the night, let's say from 9pm to 8am. How could i do it? Maybe using anacron?

Thanks,
MC[/QUOTE]
 If you only need to do it once, not every night, then a simpler solution would be to use "at" command. Read the manpage for at.

---

