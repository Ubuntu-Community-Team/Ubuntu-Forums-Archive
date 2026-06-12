---
title: "Using sudo/su in a script"
date: 2005-12-31
forum: General Help
---

### Post by Poornachandran on 2005-12-31
In order to write a script for shutting down the machine, I need to run it as a super user. But the problem is, when I use su/sudo in the script, it will prompt for the password. Is there any way, I can pass the password to these commands to avoid the password prompt?

---

### Post by One Quick Question on 2005-12-31
If you mean to run a privileged command with no password input, the only way I can think to do that is by SUIDing it, but that is a very, VERY bad practice for scripts from a security perspective.

Are there any alternatives you can do, like simply granting permission for users to shut down the machine? (That can be done from the Login Manager in KControl.)

---

### Post by jdong on 2005-12-31
Read
```

man sudoers

```

to find out how to add lines to /etc/sudoers that allow a predefined set of users run a predefined set of commands without prompting for a password.


You should trust your users to some degree, since extremely resourceful users will probably be able to gain greater root access to the system that isn't limited by sudo. If it's just a reboot, I'd recommend putting users that are permitted to reboot in the **operators** group, which gives them shutdown/reboot privs.

---

