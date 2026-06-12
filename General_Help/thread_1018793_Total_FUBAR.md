---
title: "Total FUBAR"
date: 2008-12-22
forum: General Help
---

### Post by lenswipe on 2008-12-22
There are seeral things currently wrong with my ubuntu system.

1: No desktop icons - for some reason when i logon i have no desktop icons neither can i rightclick on the desktop. If i press Alt+F2 and type gnome-settings-deamon the command exceutes but nothing happens to actually solve the problem. 

2: Pidgin - For some reason pidgin does not work, it will not connect to msn, IRC or any network. If i install an msn client on the same machine such as aMSN, it works great, just pidgin wont work. All other machines on my network can use pidgin fine.....

3: Users and Groups - This one is a bit more interesting. There are several user accounts listed in my Users and Groups window on ubuntu. If i delete a user, the user is removed from the list, but when i re-open the window the user re-apears. The user does not apear anywhere else on the system. If i try and create a user the user is created with no home directory, however the command line utility for adding and removing users works perfectly.

Please help, i dont know what on earth is wrong with my ubuntu system


-L

---

### Post by Insane_Homer on 2008-12-22
not much to go on so...

```
sudo aptitude reinstall gdm
```

```
sudo aptitude reinstall firefox
```

If that fails try for gdm and firefox

```
sudo aptitude purge gdm
```

then

```
sudo aptitude install gdm
```

```
sudo reboot
```

OK, so you've edited your post... no firefox problem any more, what did you do to fix that?

---

### Post by lenswipe on 2008-12-22
> **Insane_Homer said:**
> 

OK, so you've edited your post... no firefox problem any more, what did you do to fix that?

Yeah, i ran 

```
sudo apt-get install firefox
```

That seemed to fix it....

dont know about the flash though, you got any ideas about the pidgin thing?


-L

---

