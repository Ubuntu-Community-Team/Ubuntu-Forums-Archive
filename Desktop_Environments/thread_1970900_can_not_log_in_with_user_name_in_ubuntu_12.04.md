---
title: "can not log in with user name in ubuntu 12.04"
date: 2012-05-01
forum: Desktop Environments
---

### Post by ramazani on 2012-05-01
hi i insttaled ubuntu 12.04 on my lenovo g570 with intel i core5 , i try to sign in i put exactly the password but it said wrong so i googled some information i reset password by going to recovery mode , when i try to sigh in again it accept a password but after 2 second goes back to log in and ask me to sign in again anytime i do that it the same, only i can use guest log in is there anyway to sort it out without reinstall again

---

### Post by thenoone on 2012-05-02
Hi I have this problem as well. I upgraded from 11.10 to 12.04 and after that every time I try to login using my username and password, as well as using my fingerprint, my credentials are accepted but after that I see a black screen with some info in there and immediately goes back to the log in screen. I have tried removing the nvidia current drivers but the same happens. then tried with the nvidia again but nothing changed. I believe this happened because I tried to install the nvidia current upgrade drivers after that I get this happening.

---

### Post by ramazani on 2012-05-02
> **thenoone said:**
> Hi I have this problem as well. I upgraded from 11.10 to 12.04 and after that every time I try to login using my username and password, as well as using my fingerprint, my credentials are accepted but after that I see a black screen with some info in there and immediately goes back to the log in screen. I have tried removing the nvidia current drivers but the same happens. then tried with the nvidia again but nothing changed. I believe this happened because I tried to install the nvidia current upgrade drivers after that I get this happening.

well i just been looking for the isur on google but no chance had enough as i had dual boot with windows 7 i deleted the ubuntu and install new one now is fine

---

### Post by nuclearj on 2012-06-20
Hey did you guys figure out the solution?  This happens to me too.

---

### Post by zombifier25 on 2012-06-21
This seems to be a fairly common problem. This solution worked for me:
Press Ctrl+Alt+F1 to get into tty1, log in, and run this command:
```
sudo chown yourusername:yourusername ~/.Xauthority
```

---

