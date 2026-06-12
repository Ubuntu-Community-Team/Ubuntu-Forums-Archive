---
title: "home directory  help"
date: 2008-12-02
forum: General Help
---

### Post by emster on 2008-12-02
Okay so I got my cousin's used laptop and it just happens to have Linux on it. I have never used this system at all and I had no idea how to use it. He had a username on it and I wasn't able to change it, just my real name. Well, I thought that I wasn't doing it right so I changed the home directory from his user name to what I wanted (/home/hisusername to /home/whatiwanted). After I changed it, the internet wasn't working so i shut the computer down and now when I try to log in there is a message that says the home directory doesn't math user name. I log in and nothing but the desktop loads (no applications, places, or system menu).Does anyone know how I can change the home directory back to what it was using the root menu (which I dont know how to use either)? 
Thank you!

---

### Post by LepeKaname on 2008-12-02
Hi,

In the login screen, look for: "Console login" or something similar. Then write down the username and password.
If you know linux commands, skip this:
Once you are logged, type: "cd /home" 
then type: "mv NEWUSER OLDUSER"
where NEWUSER is the new home name you wrote, and OLDUSER the one that was it.

Thats all.

---

