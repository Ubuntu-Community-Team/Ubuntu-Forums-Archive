---
title: "Problem with Root Password"
date: 2005-10-16
forum: Desktop Environments
---

### Post by sjpritch25 on 2005-10-16
First of all, I am a linux newbie.  Breezy Badger was the only one to recognize all my hardware.  So, I installed it with three partitions.  First partition is root with the ext/3, second partition is /home with the ext/3 and a 2.5Gb swap file.  All partitions are logical.  However, doing installation it never asked me to make my Root password.  All it asked for was my user.  Please help.  I don't no what to do.  :rolleyes:   I need the root password to install java runtime for firefox.

---

### Post by mrcbrown on 2005-10-16
[QUOTE=sjpritch25]First of all, I am a linux newbie.  Breezy Badger was the only one to recognize all my hardware.  So, I installed it with three partitions.  First partition is root with the ext/3, second partition is /home with the ext/3 and a 2.5Gb swap file.  All partitions are logical.  However, doing installation it never asked me to make my Root password.  All it asked for was my user.  Please help.  I don't no what to do.  :rolleyes:   I need the root password to install java runtime for firefox.[/QUOTE]

In the Ubuntu world the suggested method of running as root is using sudo

```
sudo command
```

If you REALLY want to set a root password so you can do:

```
sudo passwd root
```

But honestly, sudo should do everything you need to do for installs, etc.

---

### Post by jasay on 2005-10-16
To clarify, use sudo and when it asks for a password, use your own user password.

---

### Post by Iandefor on 2005-10-16
In Ubuntu, the root account generally does not get used at all. If it asks for your password, enter the password of the currently logged-in user. If that fails, go to system->administration->users and groups. Under the Users tab, check "Show all users and Groups", select user "Root" and click on Properties. Under tab Account, set your password.

BTW, how much RAM do you have? Under no circumstances should you ever need a 2.5 gigabyte swapdisk.

---

### Post by brentoboy on 2005-10-16
The wiki explains it best...

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by sjpritch25 on 2005-10-17
Thanks for the advise
I am having trouble installing Java plugin for firefox
Could you please help me
Be gentle because this is my first time using linux:rolleyes:

---

