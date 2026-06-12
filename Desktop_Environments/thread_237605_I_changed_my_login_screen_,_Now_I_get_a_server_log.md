---
title: "I changed my login screen , Now I get a server login"
date: 2006-08-16
forum: Desktop Environments
---

### Post by jimmyd636 on 2006-08-16
How can I change this back from a command line, I must have checked the wrong item in the login manger . I was tring to make the auto login work. I searcjed the forms no luck. I hope im allowed to post here.
                 Thank Jim

---

### Post by Ramses de Norre on 2006-08-16
Of course you're allowed to post, why wouldn't you..
But you'll need to give a bit more info, like what did you change? When dropped to a terminal can you run ```
ps -aef|grep -i gdm
``` and see what output you get (to see whether gdm is started), the output of ```
ls /etc/rc2.d/|grep -i gdm
``` is also useful.

---

### Post by jimmyd636 on 2006-08-16
Im having trouble with the code  I need some info. In the 

   ps -aef   what is the next chater in that code  Is it a straight line?  I can't find that on my key board.
                  Thanks
                    Jim

---

### Post by jimmyd636 on 2006-08-16
Ok I found the right key for the code.

Heres what I got.

 With the first code The ps code

 root 4266  1  0 14:35 ?  00:00:00 /usr/sbin/gdm
 root 5157 4266  0 14:36 ?  00:00:00 /usr/sbin/gdm
 root 5160 5157  0 14:36 tty1   00:00:00 /usr/bin/X :0 -br -audit 0 -auth/
var/lib/gdm/:0.Xauth -nolisten tcp vt7

  gdm 5173 5157 0 14:36 ?  00:00:00 /usr/lib/gdm/gdmchooser

  jim 5218 5174 0 14:43 tty1  00:00:00 grep -i gdm

  
second code says   S13gdm

---

### Post by Ramses de Norre on 2006-08-16
That looks all OK, what exactely did you change in the gdm setup?

---

### Post by jimmyd636 on 2006-08-16
I was in gnome desk top and. Where you make it auto login. There was a box to check for I guess a server login. Not sure what I changed. but when you boot  it gives you a looking for hst login box

---

### Post by jimmyd636 on 2006-08-16
If I could just get back to the desk top Im sure I can fix it

---

