---
title: "Cant get in the Login Screen Setup?"
date: 2006-09-21
forum: Desktop Environments
---

### Post by Darell on 2006-09-21
when I try to run the program via the terminal i get this:

```
darell@Bora:~$ gksudo gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.
```

Starting via System tab ---> Adminstration ---> Login Window also doesnt work?
Can anyone help me with this?

---

### Post by aysiu on 2006-09-21
Have you tried this? ```
sudo apt-get install --reinstall gdm
```

---

