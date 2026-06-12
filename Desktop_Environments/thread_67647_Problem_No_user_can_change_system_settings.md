---
title: "Problem: No user can change system settings"
date: 2005-09-20
forum: Desktop Environments
---

### Post by Ron on 2005-09-20
I was called in to set up isp access on a newly installed Hoary Hedgehog
machine, but I found that accessing all the setup fns, such as network
controls, didn't work from any user. A password box came up, but when
a password was entered, it said, either that you are rejected, or else
it said the program terminated with exit 1.

By editing control files I was able to allow root logins, so I could do some
setup work, but obviously this won't do in the long run because the owners
can't even connect to the network without first logging in as root. I checked
the permissions for all users and found that all of them are checked as being
allowed to do everything, which makes it all the more puzzling.

Thanks for any ideas!

---

### Post by Xian on 2005-09-20
[QUOTE=Ron]A password box came up, but when
a password was entered, it said, either that you are rejected, or else
it said the program terminated with exit 1.[/QUOTE]
This is most likely due to the user changing their group settings,
which in turn affected their ability to use the sudo function.

There are remedies for this posted in the forums.

Access to root privi's in Ubuntu is available via sudo.
So, to get admin rights in gedit for example:

$ sudo gedit /etc/fstab

And so on....
Test this out in a terminal and see if the error can be duplicated.

---

### Post by Ron on 2005-09-22
sudo doesn't work, although su does, and I have managed to enable root logins, so I can operate from there. But that doesn't help with the original problem. Obviously Ubuntu isn't designed to make it impossible for users to change settings, so what could possibly be changed from a base install? Where do I look to work out what is wrong?

---

### Post by codejunkie on 2005-09-22
[QUOTE=Ron]sudo doesn't work, although su does, and I have managed to enable root logins, so I can operate from there. But that doesn't help with the original problem. Obviously Ubuntu isn't designed to make it impossible for users to change settings, so what could possibly be changed from a base install? Where do I look to work out what is wrong?[/QUOTE]
you have to add the users account to the /etc/sudoers file run this command in a terminal as root
```
export EDITOR=gedit && visudo
```
and add this to the bottm of the file
```
yourusername ALL=(ALL) ALL
```
save and exit gedit and test your apps that require sudo again let me know if this fixes it.

---

