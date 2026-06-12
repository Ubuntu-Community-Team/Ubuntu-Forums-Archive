---
title: "Can't install easyubuntu cause i don't know the root password"
date: 2006-02-21
forum: Desktop Environments
---

### Post by ksmc on 2006-02-21
when installing ubuntu i only got the chance to make a user account so have no idea what the root password is. how do i find out?

---

### Post by kaamos on 2006-02-21
Hello!

instead of
```
$ su
# command
```
do
```
$ sudo command
```

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by larsemil on 2006-02-21
and when asked for password give your password and not the rootpassword.

---

### Post by Iandefor on 2006-02-21
[quote=ksmc]when installing ubuntu i only got the chance to make a user account so have no idea what the root password is. how do i find out?[/quote] The root account is the administrator account in Unix operating systems. Because it can pose a serious security risk if somebody gets into the root account, Ubuntu leaves the root account disabled by default. Instead, it uses a program called sudo, which lets you execute a command with root priveleges. Ubuntu sets the password for sudo to be whatever your password is. If you need to install easyubuntu, preface the command to install it with sudo.

---

### Post by ksmc on 2006-02-21
i'm not using the command line. i extracted the archive and double-clicked the file called 'Easy Ubuntu' on my desktop. it specifically asks for the root password. when i input my user password is says it is the wrong password.

i don't see any documantation for easyubuntu. perhaps i'm doing it the wrong way.

---

### Post by Iandefor on 2006-02-21
A search turned up this:

[http://ubuntuforums.org/showthread.php?t=127296](http://ubuntuforums.org/showthread.php?t=127296)

Maybe that will help?

---

### Post by uqdroma on 2006-02-22
Hello, nice to meet everyone.

For my very first post I will show how to easily change the Ubuntu root password to whatever you desire.  

*WARNING* This has only been tested as working on Ubuntu Live.  I needed the live distro for a quick fix and happened to notice the disabled "rootness"  After reading the above posts I happened to try this... :-k 

```
sudo su
```

Then immediately initiate...

```
passwd root
```

And voila you can enter a new password for root.  \\:D/

Remember this needs to be done again if the live distro is rebooted.

---

### Post by Shikai on 2006-02-22
Just do 'sudo -s' from the terminal, then run easyubuntu from there.

---

### Post by MikeMcKay on 2006-02-23
uqdroma,

I had a very similar problem with a different application installation.  The root account and its password seems to be needed more frequently than envisaged by Ubuntu.

Your solution hit the spot.

Thanks,

---

### Post by ksmc on 2006-02-23
thank you Shikai. that worked.

---

### Post by jchau on 2006-02-23
[QUOTE=uqdroma]Hello, nice to meet everyone.

For my very first post I will show how to easily change the Ubuntu root password to whatever you desire.  

*WARNING* This has only been tested as working on Ubuntu Live.  I needed the live distro for a quick fix and happened to notice the disabled "rootness"  After reading the above posts I happened to try this... :-k 

```
sudo su
```

Then immediately initiate...

```
passwd root
```

And voila you can enter a new password for root.  \\:D/

Remember this needs to be done again if the live distro is rebooted.[/QUOTE]


Or you can just do a
```
sudo passwd root
```

---

