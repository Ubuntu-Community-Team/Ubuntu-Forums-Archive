---
title: "Proper way to change a hostname?"
date: 2005-11-10
forum: Desktop Environments
---

### Post by mad_pheonix on 2005-11-10
Hi,
  I'm wondering what the "preferred" method of changing the hostname in Breezy is.  The trouble I'm having is that the system relies so heavily on sudo, and whenever I try to change the hostname, I immediately get and error saying that gethostname() failed whenever I try to run sudo.  On any other system, I would first change the hostname by running the hostname command, i.e.

```
sudo hostname madphoenix
```

And then...

```
sudo gedit /etc/hosts
```

And modify the host line.  Problem is, because I need super-user access to perform both of those operations, the completion of one makes it impossible for me to do the other.  For example, if I run sudo hostname and change the hostname there, it won't let me sudo gedit because it can't run gethostname() for sudo.  Same thing when I reverse the order.  

This problem has been particularly frustrating for me because during install I wasn't able to use my University's wireless network because it has a captive portal that you need to log into through a browser before it lets any other network traffic through.  That forced me to use a university ethernet cord which had a specific assigned hostname that i don't want to use anymore.  

Any help would be greatly appreciated.  Thanks!

--mad_phoenix

---

### Post by heimo on 2005-11-10
How about:
```
sudo -s
hostname madphoenix
gedit /etc/hosts


```
FIrst become root (sudo -s), then do the changes and test on another terminal window. Once you know it works, you can exit the "super user" terminal.

---

### Post by bliffle on 2007-11-27
I have a similar problem. I changed the hostname with:

```
sudo hostname BBB
```

I exited the terminal session to see if the CLI prefix was changed, and I can't start a terminal session again.

---

