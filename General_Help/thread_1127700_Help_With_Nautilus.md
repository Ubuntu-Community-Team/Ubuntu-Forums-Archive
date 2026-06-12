---
title: "Help With Nautilus"
date: 2009-04-16
forum: General Help
---

### Post by ismialexis on 2009-04-16
Nautilus could not create required folder "/home/Alexis/ desktop" before running Nautilus please create the folder or set permission such that nautilus can create

I tried reinstalling it
I tried gksudo and sudo apt get install nautilus

nothing is working
please help

---

### Post by riza hylviu on 2009-04-16
that is stange..try starting nautilus from the terminal - sudo nautilus

---

### Post by ismialexis on 2009-04-16
do you know how i enable user sharing or how i can change settings with nautilus

---

### Post by riza hylviu on 2009-04-16
no sorry

---

### Post by ismialexis on 2009-04-17
I keep getting this message every time i start my computer

Nautilus could not create the required folder "/home/alexis/desktop".
before running nautilus please create the following folder or set permissions such that nautilus can create it

I tried gksu, gksudo , sudo nautilus in a termninal and nothing worked

this all happened after i updated stuff using update manager

i cant do anything on my computer i cant get on firefox i cant get on skype or anything and my icons arent showing
what can i do?

thanks in advance

---

### Post by danwood76 on 2009-04-17
The premissions might be messed up on your desktop folder or the folder is gone.

first try this to create the folder:
```

mkdir ~/Desktop

```
if you get permission denied or some other error you should run this to reset the owner:
```

sudo chown $USER:$USER ~/Desktop

```

regards,
Danny

---

### Post by ismialexis on 2009-04-17
i dont have that squiggly thing the one before / on my keyboard

I get this error message on my home screen every time i turn my computer on:
Nautilus could not create the required folder "/home/alexis/desktop".
before running Nautilus please create the following folder or set [ermissions such that nautilus can create.

The internet is connected but i cant use anything like skype or browse the internet. Also the icons dont show up.
what can i do

thanks in advance

---

### Post by danwood76 on 2009-04-17
Well if the terminal is fresh (as in you havent done anything) it is not needed.
So the two commands are like so:
```

mkdir Desktop
sudo chown $USER:$USER Desktop

```

---

### Post by danwood76 on 2009-04-17
Please dont start multiple threads!

---

### Post by ismialexis on 2009-04-17
Can i use something other than nautilus ?

---

### Post by Sef on 2009-04-17
merged multiple threads.

---

