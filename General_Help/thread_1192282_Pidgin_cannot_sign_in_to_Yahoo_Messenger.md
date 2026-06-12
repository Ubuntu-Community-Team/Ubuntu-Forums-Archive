---
title: "Pidgin cannot sign in to Yahoo Messenger"
date: 2009-06-19
forum: General Help
---

### Post by IsaacClarke on 2009-06-19
[SIZE=4]Pidgin 2.5.5 can't [/SIZE][SIZE=4]sign to Yahoo Messenger all of a sudden. I just turned on my computer one morning and it wouldn't log in. It's perpetually stuck in "Connecting", no error messages or anything. XFire still works using the Gfire plugin. I'm using Jaunty. 
[/SIZE]

---

### Post by jmszr on 2009-06-19
IsaacClark,

This thread will help you out: [http://ubuntuforums.org/showthread.php?t=1191064](http://ubuntuforums.org/showthread.php?t=1191064)

---

### Post by zeroseven0183 on 2009-06-20
This is what I did and it worked (thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=1006172&highlight=Pidgin"))

1. Open Terminal
2. type in 
```
sudo gedit /etc/hosts
```
3. add this in the end of the hosts
**66.163.181.184 scs.msg.yahoo.com**
4. Save and Close
5. restart Pidgin

---

### Post by IsaacClarke on 2009-06-20
> **zeroseven0183 said:**
> This is what I did and it worked (thanks [this thread]("http://ubuntuforums.org/showthread.php?t=1006172&highlight=Pidgin"))

1. Open Terminal
2. type in 
```
sudo gedit /etc/hosts
```3. add this in the end of the hosts
**66.163.181.184 scs.msg.yahoo.com**
4. Save and Close
5. restart Pidgin

This worked. Thanks to both of you.

---

### Post by Carn443 on 2009-06-20
Thanks, that helped me as well.

---

### Post by juwaini on 2009-06-20
> **zeroseven0183 said:**
> This is what I did and it worked (thanks [this thread]("http://ubuntuforums.org/showthread.php?t=1006172&highlight=Pidgin"))

1. Open Terminal
2. type in 
```
sudo gedit /etc/hosts
```3. add this in the end of the hosts
**66.163.181.184 scs.msg.yahoo.com**
4. Save and Close
5. restart Pidgin

Thanks... :lolflag:

---

### Post by siddartha on 2009-06-20
Isn't this the best sign of a software that should be avoided? This doesn't happen with the official client, and, although good parts are done by reverse engineering, gaim, pidgin, whatever they might call it the next 6 months can't cope with it. I know the answer is the reverse engineering was done by other people and the "chief" now only bothers with the Google conectivity, but shouldn't the community support something else?

---

### Post by ysNoi on 2009-06-20
> **zeroseven0183 said:**
> This is what I did and it worked (thanks [this thread]("http://ubuntuforums.org/showthread.php?t=1006172&highlight=Pidgin"))

1. Open Terminal
2. type in 
```
sudo gedit /etc/hosts
```
3. add this in the end of the hosts
**66.163.181.184 scs.msg.yahoo.com**
4. Save and Close
5. restart Pidgin

Thanks for the tips..! It worked for me as well.....!

---

### Post by inhalm on 2009-06-20
thanks its work...it work in pidgin,kopete gaim and adium

---

### Post by hootergrl123 on 2009-06-21
This worked wonders!! Thank you for the help!:KS:KS:KS:KS:KS

---

### Post by dontgetshocked on 2009-06-27
> **zeroseven0183 said:**
> This is what I did and it worked (thanks to [this thread]("http://ubuntuforums.org/showthread.php?t=1006172&highlight=Pidgin"))

1. Open Terminal
2. type in 
```
sudo gedit /etc/hosts
```
3. add this in the end of the hosts
**66.163.181.184 scs.msg.yahoo.com**
4. Save and Close
5. restart Pidgin

Thanks so much it worked for me.

---

### Post by InvisibleMind on 2010-03-23
I'm trying but

[email]my_theology@yahoo.com[/email] disabled
Error 1013: The username you have entered is invalid.  The most common cause of this error is entering your email address instead of your Yahoo! ID.
What wrong?

---

### Post by prashantkumarha on 2010-05-10
> **InvisibleMind said:**
> I'm trying but

[EMAIL="my_theology@yahoo.com"]my_theology@yahoo.com[/EMAIL] disabled
Error 1013: The username you have entered is invalid.  The most common cause of this error is entering your email address instead of your Yahoo! ID.
What wrong?


Put my_theology  only

---

