---
title: "how to make sudo not have a password"
date: 2006-09-21
forum: Desktop Environments
---

### Post by jimmyp on 2006-09-21
How do I make sudo not ask for a password for a certain user?

I tried adding this to /etc/sudoers but it doesn't work all the time, just sometimes:

$USER $HOST = NOPASSWD:ALL

---

### Post by jdunn on 2006-09-21
I'm not sure but if you are tired of entering a password for every command, you can simply create a root terminal with 'sudo -i' or you can 'sudo passwd'.  The later will allow you to create a root terminal with the 'su' command (essentially the same as 'sudo -i'

---

### Post by jimmyp on 2006-09-22
I don't want to do that because then every command that I run will be as root.  I want to have a terminal open where I run the majority of the commands as a user and occasionally need to run a command as root, with sudo.  I know the security risks but have decided that they are worth the convenience.

---

### Post by ebash on 2006-09-22
Here is how to do it, assumming that your user name id 'dude':

```
dude ALL=(ALL) NOPASSWD: ALL
```

If you trust all users in your 'admin' group you can also use:
```
%admin ALL=(ALL) NOPASSWD: ALL
```

---

