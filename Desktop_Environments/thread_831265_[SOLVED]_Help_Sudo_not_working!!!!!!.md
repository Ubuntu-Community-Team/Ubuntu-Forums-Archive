---
title: "[SOLVED] Help Sudo not working!!!!!!"
date: 2008-06-16
forum: Desktop Environments
---

### Post by shawnansasio on 2008-06-16
Okay, so i just installed ubuntu on vmware workstation (windows).
And i Accdently removed /etc/sudoers.
So i try to copy sudoers from one of my computers that actually has ubuntu on it via. usb mem stick. and when i remove my mem stick form the computer (The real ubuntu one) sudo wont work!!

Here's what happens:

# sudo -l
sudo : /etc/sudoers is mode 0660, should be 0440.



HELP PLEASE

Ps, Here is my sudoers file:


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults    !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
shawn   ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


Pss. My username is shawn

---

### Post by aysiu on 2008-06-16
Boot into recovery mode and type ```
chmod 0440 /etc/sudoers
shutdown -r now
``` If you don't know how to boot into recovery mode, look at the first two images in [this tutorial](http://www.psychocats.net/ubuntu/resetpassword).

---

### Post by shawnansasio on 2008-06-16
Ummm... Sorry I am running on a work computer so i can not reboot in to restore mode or what ever you call it because if i do a bunch of people will lose their work.

However I now have the root password and i tried the command as root and heres what came up.

# chmod 0440 /etc/sudoers
# sudo -l
sudo : /etc/sudoers is owned by gid 1010, should be 0

Is there anyway i could fix it without rebooting?
Sorry i am causing so much trouble.        :(


Ps. Notice how i could not reboot.                 :lolflag:

---

### Post by Zorael on 2008-06-16
edit: I read it again. Do this.
```
# chmod 0440 /etc/sudoers
# chown root:root /etc/sudoers
```



Old post:> I don't think you can.

The /etc/sudoers file *must* be 0440 (read and execute by user root and group root, inaccessible to others) for sudo to play nice. You're in a [catch 22](http://en.wikipedia.org/wiki/Catch-22); you need sudo to correct the permissions of /etc/sudoers, but sudo won't since the permissions of /etc/sudoers are wrong.

The easy way is, as already suggested, to boot into recovery mode and change it from there.

---

### Post by aysiu on 2008-06-16
You don't reboot your entire computer. Since Ubuntu is installed in VMWare, just reboot the virtual machine and select Recovery Mode.

Since you seem to be able to log in as root, you can do ```
chown root:root /etc/sudoers
chmod 0440 /etc/sudoers
```

---

### Post by shawnansasio on 2008-06-16
Yo Zoreal, I sorta did not listen to you and tried the commands as root and I have two things to say to you:


1.THANK YOU SO MUCH!!! (The commands worked as root)

2.I KNEW THERE WAS A WAY TO DO IT WITHOUT REBOOTING!!!!!


Anyway, YOU ROCK!!!!!!!!!!!!!

Man if my dad caught me I would of ben grounded for a month!!!


Ps,aysiu you rock to

---

### Post by shawnansasio on 2008-06-17
Ummm... aysiu sorry for the miss understanding it is not the vmware machine that is not working it is the real ubuntu machine that is not working.    :guitar:

---

