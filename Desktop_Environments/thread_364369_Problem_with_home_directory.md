---
title: "Problem with home directory"
date: 2007-02-18
forum: Desktop Environments
---

### Post by afham07 on 2007-02-18
hi guys,

last nite, i played around with user & group setting and i changed my home directory from to root. originally, it is /home/afham07. Now, I cannot login my afham07 profile. I also cannot login root because i do not enable root login.

Is there any way to edit the home directory in user & group setting using CLI?

I tried by add new user but the new user is not super user. So, it cannot access to administration control. What should i do guys?

I have 3 ways to solve my problem but I have limited knowledge of command. 1st, edit home directory of afham07 by using CLI. 2nd, create new user and set it as super user. I already added new user but it is not super user. what is the command to set a user to super user? 3rd, enable root login by using CLI. 

FYI, I still new in Linux. Just install a few days ago. I really appreciate if any1 here can show my the solution step by step.


TQ.

---

### Post by yabbadabbadont on 2007-02-18
Reboot and take the "recovery mode" option.  Once at the command prompt, use usermod to change the home directory of afham07.

usermod -d afham07 afham07

Then make sure that the /home/afham07 directory permissions are correct.

chown -R afham07:afham07 /home/afham07

After that just type, "reboot", (without the quotes) to reboot your system.  You should be able to login after that.

---

### Post by frafu on 2007-02-18
I am moving this thread to a more appropriate forum. 

Have a nice day.

---

### Post by afham07 on 2007-02-18
arghh..

i tried the chown method but it does not working. I think, maybe I putted wrong home directory. Is there any way to search for home directory?

How to set a normal user to become super user by using CLI? I tried this command but does not work: adduser afham root ... It means I add my normal user (afham) into root group but it still remain as normal user.

---

### Post by googanhiem on 2007-03-04
I believe there was a small misprint in this fix. Also make sure you're working under the root user.

usermod -d /home/afham07 afham07

then

chown -R afham07:afham07 /home/afham07

I know this sounds stupid but remember unix is case sensitive, so that R must be a cap. Good luck.

---

