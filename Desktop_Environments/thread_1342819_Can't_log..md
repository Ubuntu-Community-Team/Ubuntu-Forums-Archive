---
title: "Can't log."
date: 2009-12-01
forum: Desktop Environments
---

### Post by abriotde on 2009-12-01
Hello,

I am very happy with ubuntu. Thank you. But I accidently remove all the content of /home/alberic (running 'sudo rm -r /home/alberic/*') from an administrator account 'surget'. Now I can't log under gnome. I manage to log on with 'surget' (administrator) and even with the other account 'invite' (low permission). From an account I manage to log with ssh to 'alberic' (running 'ssh alberic@localhost'). 

Thank you for any help.
Albéric.

---

### Post by dvlchd3 on 2009-12-01
There are many files that are essential for your user stored in your home directory.  (You do not see them because they are hidden...)  You are probably going to have to remove the user account and add it back.

```

rmuser alberic
useradd alberic

```

Once you create the user run this command to see all the hidden directories:

```

ls -sail /home/alberic | grep '^.'

```

Keep this in mind anytime you want to recursively delete a directory!

---

