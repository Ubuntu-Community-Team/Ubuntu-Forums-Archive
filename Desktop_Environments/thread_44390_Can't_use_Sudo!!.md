---
title: "Can't use Sudo!!"
date: 2005-06-25
forum: Desktop Environments
---

### Post by vtechstu on 2005-06-25
Ok i went into KUser to change my password, i selected my name, and click   configure and changed the password. 

Now when I use sudo, i get this error :

sudo: uid 1000 does not exist in the passwd file!
chase@chase:~/cvs$ sendmail: fatal: no login name found for user ID 1000

Now, I can't even get into Kuser anymore!

Nor can i use Kynaptic!!

Konsole now has this when i open it:

I have no name!@chase:~$

Help!

---

### Post by vtechstu on 2005-06-26
Don't worry about it folks, I just did a reinstall.  I don't have time to wait and figure it out, was a fresh install anyway.  Thanks

---

### Post by az on 2005-06-26
Is this a bug?


bugzilla.ubuntu.com

---

### Post by vtechstu on 2005-06-26
I don't know, you tell me, I may have very well done it wrong.  These are my exact steps.

KMenu > System > KUser > Entered Password > Selected my User Name   > Click User at top > Selected "Set Password" > Typed in the new password.

Thats it, my name was no longer visable in Konsole, and once i logged out i could no longer.  When i tried to use the old password it said fail login.  When I tried to use the new password, It said that I cannot log in as Root from there.  So, I'm not sure what  happened.  

For the record, how does one change their password the correct way, so I don't jack up my partition again. 

Thanks.

---

### Post by zeddemore on 2005-06-26
I just tested these steps and I didn't have this problem. My (K)Ubuntu is fully updated with security updates. And yours?

---

### Post by Firetech on 2005-06-26
[QUOTE=vtechstu]For the record, how does one change their password the correct way, so I don't jack up my partition again.[/QUOTE]
Because you seem to be fammiliar with the console (konsole), start it and run "passwd". That's how I always do it, but I'm a console junkie...

---

### Post by vtechstu on 2005-06-27
I thought my security was updated, but maybe not.  Or maybe i have just really bad luck.

---

### Post by fdoving on 2005-06-27
There are known issues with older versions of kuser. please use the updated version.

---

### Post by vtechstu on 2005-06-27
I just tried to apt-get it and it said i already had the latest version.   So i guess it wasn't that.

---

