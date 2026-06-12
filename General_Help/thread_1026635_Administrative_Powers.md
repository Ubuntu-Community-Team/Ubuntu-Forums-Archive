---
title: "Administrative Powers"
date: 2008-12-31
forum: General Help
---

### Post by amalik on 2008-12-31
Dear all:

I just installed the Ubuntu using the Window. I want to copy a *.so file in the /lib/. At the start, the installer asked me about the user name and passowrd. However, when I tried to log in using "su", and give my password, it fails.

My question is how can I have the administartive powers? Did I skip someting when I installed it?

Any comments?

Thanks

---

### Post by sdibias on 2008-12-31
Ubuntu uses sudo rather than su by default the root account is disabled. Enter the same command using sudo in front of it and then you can elevate with the same password you use to login to Ubuntu.

Hope that helps!

---

### Post by taurus on 2008-12-31
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sdibias on 2008-12-31
Also please see

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 

Happy New Year! ;)

---

### Post by Kinetic Being on 2008-12-31
Ubuntu doesn't use "su" to get root powers, it uses "sudo" which is like su except for a single command. 

Preface your command with sudo, and it will be done with root privlages.

If you want to open a terminal as root, you can use "sudo bash"

---

