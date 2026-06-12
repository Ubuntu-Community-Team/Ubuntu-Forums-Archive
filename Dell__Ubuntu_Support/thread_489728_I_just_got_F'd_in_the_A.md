---
title: "I just got F'd in the A"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by 3th0s on 2007-07-01
So currently my problem is that when I log in, the screen just freezes, and i'm forced to restart/shut down.
The last thing I was doing was trying to tinker with enabling WPA [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")
. The last two things i did was edit the file under /etc/network/interfaces , by putting a '//' before every line except the first two. After that, I tried creating the file under /etc/default/wpasupplicant, but wasn't quite sure how to do that. I tried logging out, and then logging back in as root, but it says you can't log in as root from the login screen. So i simply rebooted, and then thats where the problem began. 

I'm currently using the ubuntu install disk (i loaded under rescue mode, but it looks suspiciously similar to the normal 'live disk' ubuntu during the pre-install) just to use firefox, and i'm really lost. I have no idea how to even get in,let alone how to try and backtrack. Any hlep would be great!
Thanks,
-3th0s

---

### Post by 3th0s on 2007-07-01
K so i found out how to log in under failsafe terminal-only mode, but i really have no idea where to go from here. I've tried to re-edit the file under /etc/network/interfaces, but everytime i try, it asks for password which i put in, and then freezes. If i log in as root in the terminal, and then try to gedit, it tells me "gtk-warning: cannot open display", which im guessing is because im in safe terminal-only mode. 

I honestly have no clue where to go...
-3thos

---

### Post by radeon21 on 2007-07-01
what sort of hardware are you running on?  what sort of configuration did you do before trying to configure wpa?

---

### Post by 3th0s on 2007-07-01
I'm running  intel on an inspiron 9300. I hadn't really done anything with the wireless since i installed ubuntu, i just switched from fedora, and just kind of assumed that some work had to be done to get wireless up and running. Other than the debain WPA walkthrough's first 4 steps prior to the meltdown, i haven't done anything with regards to wireless or even networking.

---

### Post by khedron on 2007-07-01
If you want to edit the file while in terminal mode, try using nano:
```
nano /etc/netwok/interfaces
```
It behaves as much like a normal text editor as it can - no weird key combinations (I'm looking at you, Vim!).

---

### Post by kerry_s on 2007-07-01
> **khedron said:**
> If you want to edit the file while in terminal mode, try using nano:
```
nano /etc/netwok/interfaces
```
It behaves as much like a normal text editor as it can - no weird key combinations (I'm looking at you, Vim!).

it's->
**sudo nano /etc/netwok/interfaces**

---

### Post by khedron on 2007-07-01
It's actually
```

sudo nano /etc/network/interfaces

```Two typos in the same line... I'm getting tired. It's past my bedtime.

---

### Post by 3th0s on 2007-07-02
Thanks a lot, got it working again!

---

