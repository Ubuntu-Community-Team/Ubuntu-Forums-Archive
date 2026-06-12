---
title: "auto login not working after logout"
date: 2012-01-27
forum: Desktop Environments
---

### Post by ProntoAnthony on 2012-01-27
I have a desktop and a laptop running 11.10. Both have just 2 users configured, Anthony and backup. User Anthony is set for auto-login. 
When I logout of my laptop, a login page appears with the password field set to LOGIN. I simply click and I'm logged in as I'd expect.

Likewise, when I boot my desktop I'm logged in automatically to the Anthony account. When I logout the password field is blank. Clicking to login causes the system to respond with "invalid password." Sure, I can key in the password and login successfully, but why must I enter a password in those cases?

I even tried setting the backup account to auto-login and going through the process. The desktop system responded the same incorrect manner, requiring a password upon login.

How do I fix this problem?

---

### Post by Krytarik on 2012-01-27
That's because the user "Anthony" is apparently set to 'no password on login' in one system, but not in the other. Unfortunately, as of now, Gnome 3 doesn't offer that option via its "User Accounts" tool, but you can manually add the concerning user to the group "nopasswdlogin" via command line; in your case:
```
sudo usermod -a -G nopasswdlogin anthony
```Regards.

---

### Post by ProntoAnthony on 2012-01-27
That worked.

THANK YOU!!

---

