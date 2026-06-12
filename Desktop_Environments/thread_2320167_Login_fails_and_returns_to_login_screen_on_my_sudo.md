---
title: "Login fails and returns to login screen on my sudo machine, but ok on other machines"
date: 2016-04-11
forum: Desktop Environments
---

### Post by yuval.aft on 2016-04-11
I am using a machine on a cluster with a shared filesystem.
On one of these machines I have a sudo account with ubuntu 14.04 installed.


The problem is that login fails and returns to login screen on my sudo machine, while login is successful on other machines that I don't have a sudo on. This means that the issue is specific to my machine, and unrelated to files on my homedir. Login also fails when I try to connect with a local user.


login is successful with tty mode. I tried ```
sudo apt-get install --reinstall ubuntu-desktop
``` and reboot, but it didn't help




Thank you

---

### Post by grahammechanical on 2016-04-11
I do not know what you mean by "sudo account." Are you saying that when you log in to this machine the login fails even though the correct password is being used and yet when you go to tty1 you can log in to the Linux command line with the same password?

Regards

---

### Post by yuval.aft on 2016-04-11
> **grahammechanical said:**
> I do not know what you mean by "sudo account." Are you saying that when you log in to this machine the login fails even though the correct password is being used and yet when you go to tty1 you can log in to the Linux command line with the same password?

Regards

1. Yes about tty1.

2. By sudo account I mean that on this specific machine I also have super user privileges.

3. On the other machines, I don't have super user privileges, yet I can login as usual

Thank you

---

### Post by grahammechanical on 2016-04-12
Have you seen the second post in this thread? I do believe the advice given there is the solution

[http://ubuntuforums.org/showthread.php?t=2320254&p=13469203#post13469203](http://ubuntuforums.org/showthread.php?t=2320254&p=13469203#post13469203)

Regards.

---

