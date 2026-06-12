---
title: "Root = none"
date: 2007-06-09
forum: Desktop Environments
---

### Post by NJC on 2007-06-09
How do I bring back the proper root? If I open a terminal I see <name>@(none) instead of desktop. 

I can't run sudo, or almost anything from System/Admin. I inadvertently changed the Location under Networking but not sure if that's the problem.

Suggestions appreciated.

---

### Post by llamakc on 2007-06-09
> **NJC said:**
> How do I bring back the proper root? If I open a terminal I see <name>@(none) instead of desktop. 

I can't run sudo, or almost anything from System/Admin. I inadvertently changed the Location under Networking but not sure if that's the problem.

Suggestions appreciated.

Are you asking about the root user or the root of the file system?

---

### Post by NJC on 2007-06-09
I (think) I mean root user. When I opened a terminal I'm sure it used to display <name>@desktop (or something similar) but now it says <name>@(none).

---

### Post by trippinnik on 2007-06-09
That's just your computer's name on the network.  to set it back or change it to something else Click "System" - "Administration" - "Network" and then choose the hostname tab.  You can change it to whatever you want there.

---

### Post by NJC on 2007-06-09
trippinnik;

That's why I've sent out this SOS - I can't access System/Admin/Networking and I'm assuming the problems of having "(none)" at the Terminal is the same problem.

EDIT: This is an example:

```

<name>@(none):/etc/X11$ sudo gedit xorg.conf
sudo: unable to lookup (none) via gethostbyname() 
```

And a Window keeps coming up - with the following under the Details tab:

```


Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host-(none)/0/numlock_on": `(' is an invalid character in key/directory names

```

---

### Post by NJC on 2007-06-09
Original poster of this thread:

[http://ubuntuforums.org/showthread.php?t=188337](http://ubuntuforums.org/showthread.php?t=188337)

had success with this fellow's advice:

[http://ubuntuforums.org/showpost.php?p=748387&postcount=13](http://ubuntuforums.org/showpost.php?p=748387&postcount=13)

**UPDATE: Resolved!**

Rebooted into Recovery mode via Grub, and then edited the the hosts and hostname files:
```

nano /etc/hosts
nano /etc/hostname
```

I ensured first 2 lines of host file were as follows:
```
127.0.0.1 localhost <myname>-desktop
127.0.1.1 <myname>-desktop
```

I also placed "<myname>-desktop" in the hostname file. This was a result of late-night fargin' around in my Syste,/Adminstration/Networking Hosts tab I think. Anyhow, don't recklessly delete Hosts

---

