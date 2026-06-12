---
title: "Help not the password thingy!"
date: 2009-04-19
forum: General Help
---

### Post by Angerflst on 2009-04-19
everyone advised me not to get into the password aspect of  the admin's password. so, i have decided to take another route. is their a way for me to make a username with admin rights. like i am on my acc but when i go to system>adminastration> then user group. it says im not allowed to. if this is anouther issue that no one can talk about then i suck at life. btw i am 18, i say this because people thought i was not in the other thread.

---

### Post by phantom3113 on 2009-04-19
When you initially install ubuntu, the first user (you I assume) is made "secondary admin" and are required to make a password. The primary admin is known as "root" and certain things in the basic ubuntu install are protected by the requirement of root priveledges, such as most things in the administration menu. The password that is asked for is the same password you made when installing ubuntu. In short, by default the root password=1st user's password. Any other users that are created after that point are automatically made as limited users, unless you add them into various groups giving them admin priviledges.

---

### Post by Angerflst on 2009-04-19
> **phantom3113 said:**
> When you initially install ubuntu, the first user (you I assume) is made "secondary admin" and are required to make a password. The primary admin is known as "root" and certain things in the basic ubuntu install are protected by the requirement of root priveledges, such as most things in the administration menu. The password that is asked for is the same password you made when installing ubuntu. In short, by default the root password=1st user's password. Any other users that are created after that point are automatically made as limited users, unless you add them into various groups giving them admin priviledges.

ok. thanks you for that clean and efficient answer.

---

### Post by phantom3113 on 2009-04-19
No problem! Just be very careful when doing anything that requires the root password. Some things, especially in the terminal, can severely harm your system up to making it unbootable.

---

