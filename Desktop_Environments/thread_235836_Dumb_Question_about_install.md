---
title: "Dumb Question about install"
date: 2006-08-13
forum: Desktop Environments
---

### Post by fixitben on 2006-08-13
I just installed ubuntu fromt the altertive .iso but during install it said use this user name the first time and the password you entered.  But I forgot what that Name was between the time it said it and when I went to login.   It was something like 'user' or something but everything I tried doesn't work.  So I was wondering if someone remebered.

Thanks
Fixitben

---

### Post by az on 2006-08-13
Boot into recovery mode and type


ls /home

and that will tell you the name of the user (the home folder is named after the user.

If you forget the password, type

passwd (user) (newpassword)

Run 

init 2

to get back into the desktop mode from recovery mode.

---

### Post by fixitben on 2006-08-13
Man I new it was easy. It was 'OEM' 

Thanks for the help

Thanks
Fixitben

---

