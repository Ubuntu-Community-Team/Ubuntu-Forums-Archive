---
title: "log in problem"
date: 2007-06-20
forum: Desktop Environments
---

### Post by Exygot on 2007-06-20
When i attempt to log into Ubuntu i get this error.

       User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by others.

after i click ok  it starts to load and i get this error

       Your session lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space.  Try logging in with one of the fail safe sessions to see if you can fix this problem.

at this point it takes me back to the login screen.  I try to use the failsafe modes but the first does nothing and the console one i do not know what i need to do on to fix this problem

---

### Post by dreadlord_chris on 2007-06-20
log into the console and post the output of the following, please:
```

ls -la

```

---

### Post by taurus on 2007-06-20
_Assuming_ your login name is **john**, boot into recovery mode and do

```
chown -R **john**:**john** /home/**john**
chmod -R 755 /home/**john**
chmod 644 /home/**john**/.dmrc
shutdown -r now
```
Now see if you still get that error message when you log in with your username from GUI login screen.

---

### Post by Exygot on 2007-06-20
hey thanks that worked splendid i am back up and operating.

Thanks

---

