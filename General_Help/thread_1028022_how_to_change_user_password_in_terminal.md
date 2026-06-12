---
title: "how to change user password in terminal?"
date: 2009-01-02
forum: General Help
---

### Post by icejack_outlaw on 2009-01-02
hi guys.... i just install ubuntu ibex in my friends desktop.... then the installation good....and i name the user is "jack" and password is abc123 for easy to remeber for a while. after installation and i reboot the pc.... i cannot login to "jack" acc...then i try login i terminal (ctrl+alt+f1)... but i dont know to reset the "jack" password... can any body help me??

for advance.... thanks alot guys

---

### Post by kgas on 2009-01-02
Passwords are case sensitive. could you try different combinations? Could you able log in thro' terminal? If so it is strange why you could in login thro' GUI?. There are may ways to reset the password.

Read this to reset user password: [http://www.cyberciti.biz/faq/linux-resetting-a-users-password/](http://www.cyberciti.biz/faq/linux-resetting-a-users-password/)

also read this: [http://rhadimas.wordpress.com/2006/10/15/reset-linux-password/](http://rhadimas.wordpress.com/2006/10/15/reset-linux-password/)

---

### Post by Tim Sharitt on 2009-01-02
Boot into recovery mode and select root terminal, then enter 
```
passwd jack
```

---

### Post by prshah on 2009-01-02
> **icejack_outlaw said:**
> but i dont know to reset the "jack" password... can any body help me??

If you have access to any other admin enabled account log into that, or if you are able to use the "sudo" password, and give the command```
sudo passwd -d jack
``` This will delete the password for user jack. If you do not have "sudo" access (or cannot login at all) then from the startup (GRUB) menu, choose recovery mode, and when loaded, give the same command as above, but leave out the "sudo".

---

