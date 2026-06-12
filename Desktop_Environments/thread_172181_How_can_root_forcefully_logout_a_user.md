---
title: "How can root forcefully logout a user?"
date: 2006-05-08
forum: Desktop Environments
---

### Post by louis_nichols on 2006-05-08
I've ben using Linux for quite a while now and I'm planning to eep doing so. I'm interested almost exclusively in Linux as a desktop environment and am very glad to have found ubuntu, which is very good for that.

But for a while I've been kinda puzzled by this question, which comes rather from the server-admin realm, but might prove useful:

So, an admin, logged in as root, or a user with sufficient privileges, detects that another user logged on the machine is doing something that's not allowed for some reason. Now, an admin must have a tool to forcefully log that user out and perhaps even close all processes started by that users's login session. How is this done?

---

### Post by cgjones on 2006-05-08
First, determine the process id (PID) of the shell they are using to login.
```
ps aux | grep *user*
```
Look for the entry for the login shell. If they are using bash, it will be the line where the last column is -bash. The number in the second column is the PID.
To kill the login shell, type the following:
```
kill *PID*
```
This should stop the user's login session. I'm not sure if this will also stop any other processes of that user, but if not, you can just use the first command again to find any other processes for the user and kill them.

---

### Post by vanadan on 2008-05-25
dosn't work.. 

```

root@bedna:/home/ivka# ps aux | grep ivka
root      7609  0.0  0.0   3004   748 pts/1    R+   18:33   0:00 grep ivka
root@bedna:/home/ivka# userdel ivka
userdel: user ivka is currently logged in
root@bedna:/home/ivka#

```

nor this:
```

root@bedna:/home/ivka# pkill -KILL -u ivka
root@bedna:/home/ivka# userdel ivka
userdel: user ivka is currently logged in
root@bedna:/home/ivka#

```

is it a bug? (using hardy heron..)

---

### Post by xentro on 2008-05-26
In this case 

"ps aux | grep ivka
root      7609  0.0  0.0   3004   748 pts/1    R+   18:33   0:00 grep ivka"

you dont have any user ivka logged in. The returned line refers to you grep command.

Anyway, if in this case it was a user's shell process you just had to do:

kill 7609

---

### Post by sisco311 on 2008-05-26
Use the *who* command to see list of logged in users and *sudo* *pkill -KILL -u username* to log out user.

---

