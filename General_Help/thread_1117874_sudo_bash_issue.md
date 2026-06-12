---
title: "sudo bash issue"
date: 2009-04-06
forum: General Help
---

### Post by GavinSpearhead on 2009-04-06
When I start sudo bash as a normal user, it seems to source the /home/user/.bashrc instead of the /root/.bashrc ; which strikes me as a bit weird. Any one know if this is intended behaviour or ...? 

I tried this on intrepid....

---

### Post by Ayuthia on 2009-04-06
sudo just gives the user admin privileges.  It does not make the user root.  So this is the intended behaviour.

---

### Post by sisco311 on 2009-04-06
> **GavinSpearhead said:**
> When I start sudo bash as a normal user, it seems to source the /home/user/.bashrc instead of the /root/.bashrc ; which strikes me as a bit weird. Any one know if this is intended behaviour or ...? 

I tried this on intrepid....

```
sudo -i
```
```
man sudo
```
> -i [command]
                   The -i (simulate initial login) option runs the shell
                   specified in the passwd(5) entry of the target user as a
                   login shell.  This means that login-specific resource files
                   such as .profile or .login will be read by the shell.  If a
                   command is specified, it is passed to the shell for
                   execution.  Otherwise, an interactive shell is executed.
                   sudo attempts to change to that user's home directory
                   before running the shell.  It also initializes the
                   environment, leaving DISPLAY and TERM unchanged, setting
                   HOME, SHELL, USER, LOGNAME, and PATH, as well as the
                   contents of /etc/environment on Linux and AIX systems.  All
                   other environment variables are removed.


---

