---
title: "Start more than 6 sessions in Ubuntu 8.10"
date: 2009-03-02
forum: Desktop Environments
---

### Post by Dacus on 2009-03-02
ello guys, i have installed on my computer Ubuntu 8.10 it is greate, for me it is the first time when i try to work on it and i like it a lot. I'm a bit of tester and i need to test some applications. I need to start more than 6 sessions but when i start the 7th session it gives the folowing message: 
  
    **Too many Sessions**

*There are curently too many sessions running to create a new one. Someone must log out, or the system configuration must be changed to allow for more.*

#Please i need to have at least 8 users loged in.


P.S.> 	
So nobody?  :(

---

### Post by veloce on 2009-03-08
> **Dacus said:**
> ello guys, i have installed on my computer Ubuntu 8.10 it is greate, for me it is the first time when i try to work on it and i like it a lot. I'm a bit of tester and i need to test some applications. I need to start more than 6 sessions but when i start the 7th session it gives the folowing message: 
  
    **Too many Sessions**

*There are curently too many sessions running to create a new one. Someone must log out, or the system configuration must be changed to allow for more.*

#Please i need to have at least 8 users loged in.


P.S.> 	
So nobody?  :(

Since nobody else is answering, I'll throw in the (very) little I know:

There is a setting for XDMCP for the number of remote sessions but the default is 16.  (This is found in System - Administration - Login - Remote - XDMCP Settings.)

How are your users getting remote access?

---

### Post by warp99 on 2009-03-09
You need to add more terminals to your /etc/inittab file since it defaults to 6 and one for x-server. So open the file as root with your favorite text editor and scroll down to this part:

```
 Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

```

Just add the additional ones you need. I'm not positive on the maximum number of terminals you can have spawned.

Edit:

I just noticed that your on Ubuntu 8.10. Well that's different since everything was migrated to the /etc/event.d folder. If you check in this folder you'll see the following files:

```
:/etc/event.d$ ls -1
control-alt-delete
last-good-boot
logd
rc0
rc1
rc2
rc3
rc4
rc5
rc6
rc-default
rcS
rcS-sulogin
sulogin
[b]tty1
tty2
tty3
tty4
tty5
tty6[/b]
```

Just open the last file named tty6 in your text editor as root, make a few changes (very obvious), then save the file as tty7 or tty8 if you use x-server. Repeat as needed for more terminals. Sorry about the confusion.

---

