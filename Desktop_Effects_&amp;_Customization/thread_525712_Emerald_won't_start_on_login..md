---
title: "Emerald won't start on login."
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by RKDN on 2007-08-14
I have just recently installed compiz fusion and it works great. Although when I set it to start by going to sessions and adding "compiz --replace -c emerald &" compiz will start but emerald doesn't. I can manualy start emerald by running "emerald --replace" after I have logged in. However if I try to set up two start up entrys like "compiz --replace" and "emerald --replace". Emerald will still not start up on login.

---

### Post by RKDN on 2007-08-14
Anyone have any ideas?? I think it may have something to do with Emerald trying to open before compiz... although I am probably completely wrong... I really need help on this. Starting Emerald on each start is a pain.

---

### Post by RKDN on 2007-08-14
Well if anyone else is having problems getting emerald to start like I did then just install the fusion icon. It was the only way I was able to get Emerald to start on boot.

---

### Post by conradlyn on 2007-08-15
i am having the somehow alike problem.

my compiz-fusion will start normally when login,but emerald just won't load any theme i did in last login,and all the thing would go back to metacity one,then i have to manage the emerald theme again to make acceptable for me each time i login.

why ?

---

### Post by njknight on 2007-08-15
I experienced the same problem and solved it by splitting the command in the session startup manager (system, preferences, sessions)

so first add an entry in the startup programs to run compiz fusion
compiz --replace -c

then add a new entry in the startup programs for emerald
emerald --replace &

No guarantees, but all I can say is this worked for me see attachments

---

### Post by lordgreg on 2007-08-16
hi! 

it works. i assume you would get the same effect with adding exact same lines in profile file or bashrc?

ty

---

### Post by sreejithr on 2007-08-22
it doesn't work for me...any ideas??

---

