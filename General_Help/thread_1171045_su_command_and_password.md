---
title: "su command and password"
date: 2009-05-26
forum: General Help
---

### Post by iochinome on 2009-05-26
hey guys, so i have a pretty beginner question here. i am just now learning about superusers, sudo, root, etc. on my computer, running jaunty, i have no problem executing commands as superuser, like typing in 
$sudo do something
(then entering in my password right here)

when installing ubuntu onto my computer, i made sure that i made all of the passwords the same, so as not to become confused. then, the other day, someone told me to try logging in as root, typing 
$su

and then it asks me for the password. well when i type in the password that i use for everything else, including when i just type in 'sudo something,' it tells me 
su: Authentication failure

how do you log into su? i dont get it... did i screw something up when installing it?

thanks!

---

### Post by amingv on 2009-05-27
su usually asks for the root password (or the password of the user you're trying to access, depending on the case), but since root is disabled by default in ubuntu, it has no password, so whatever you put there will return as an incorrect password.

If you need to use a root console, you can still do it by typing

```
sudo su
```

and typing your regular password on the prompt, just make sure to be very careful while dabbling as root.

---

### Post by pjones0404 on 2009-05-27
here is a quick link that will explain what is going on. i thought it was a pretty quick read. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There is not a root account by default in ubuntu. You can enable one but it is generally not recommended. Almost everything can be accomplished using the sudo su command.

---

