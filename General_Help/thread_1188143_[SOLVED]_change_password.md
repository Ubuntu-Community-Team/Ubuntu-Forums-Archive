---
title: "[SOLVED] change password"
date: 2009-06-15
forum: General Help
---

### Post by dec!&quot;` on 2009-06-15
Hello,
I am new to these forum.
I am running ubuntu 9.04 jaunty, on a Dell latitude D600 laptop with password's problems.
I've tried to change it, but every time I do it, i'm asked for my old password, which apparently doesn't recognize anymore.
Any ideas?

---

### Post by mhgsys on 2009-06-15
Hello, and welcome.

to recover or change password without having to use the old one.
bootup in recovery modes/ 

then 
```
 cd /home/ 
```


```


ls -a

```

You'll find your username there.
then

```


passwd username

```
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

reboot, log in with your username and passwd.

[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)
__________________

---

### Post by aysiu on 2009-06-15
For more details, with screenshots:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by dec!&quot;` on 2009-06-15
> **mhgsys said:**
> Hello, and welcome.

to recover or change password without having to use the old one.
bootup in recovery modes/ 

then 
```
 cd /home/ 
```


```


ls -a

```

You'll find your username there.
then

```


passwd username

```
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

reboot, log in with your username and passwd.

[http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)
__________________
Hey, thanks a lot!
It worked fine.

Cheers!

---

### Post by mhgsys on 2009-06-15
nice. 

Your welcome.

---

