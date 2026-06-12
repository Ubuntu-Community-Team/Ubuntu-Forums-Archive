---
title: "How to automatically login?"
date: 2011-03-08
forum: Desktop Environments
---

### Post by Physicist on 2011-03-08
I have Ubuntu 10.10 Gnome. My computer automatically boots up at a particular time of day. But it stops at the login window. 1) How do I let it automatically login? I have set passwordless login.So when I manually hit my login username, it logs in without needing me input password. But it gives a pop-up window asking for keyring password, 2) how to get rid of it?

---

### Post by drs305 on 2011-03-08
You of course will reduce the security of your system, but you can eliminate the password request by:
System > Preferences > Encryptions & Keyrings 
Right click on Password, Change Password.
Enter your current keyring password and leave the new and confirm boxes empty.

---

### Post by cap10Ibraim on 2011-03-08
try the options ins system-> administration->login screen

---

### Post by Kirboosy on 2011-03-08
> **cap10Ibraim said:**
> try the options ins system-> administration->login screen

+1 This will allow you to achieve your goal

---

### Post by drs305 on 2011-03-08
I may have misinterpreted what you wrote. If you haven't enabled the passwordless option in System, Administration by all means to that as suggested by the previous posters and see if that accomplishes what you want. That will still leave your keyring security intact if that fixes your issue. I'm sure we all recommend you disable as little as possible.

---

### Post by Kirboosy on 2011-03-08
> **drs305 said:**
> I may have misinterpreted what you wrote. If you haven't enabled the passwordless option in System, Administration by all means to that as suggested by the previous posters and see if that accomplishes what you want. That will still leave your keyring security intact if that fixes your issue. I'm sure we all recommend you disable as little as possible.

You answered question two on his OP. :)

---

### Post by Physicist on 2011-03-08
Thanks to everyone for the very quick answers. I wasn't aware that a passwordless keyring would also mean my passwords will be stored in plain text (right?) If it's that, I won't do. But I can now login without manually hitting my login user name. So thanks for that.

---

