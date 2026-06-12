---
title: "&quot;Unlock&quot; button greyed in nm-applet and users-admin"
date: 2008-07-28
forum: Desktop Environments
---

### Post by piyush_srivastava on 2008-07-28
Hello,

I use wmii, and login without using the gdm on Ubuntu(running on an IBM R52 Laptop). nm-applet used to work fine when run as sudo till I was on gutsy.

However, since an upgrade to Hardy, all the controls in nm-applet are greyed on starting it(even the Unlock button is greyed), and I cannot change any settings, even if I run it as root or with sudo. The same problem persists with users-admin. 

I read on the forums that I must add myself to the policykit group which I did, so that the corresponding line in /etc/group looks as:

```
polkituser:x:133:piyush
```

Still, the problem persists. 

I would be thankful if someone could help me to get nm-applet running, since it is much easier to use it than the method that I have to use currently to switch to WiFi(that of editing /etc/interfaces :()

Thanks,
Piyush.

---

### Post by scottuss on 2008-07-28
I had exactly the same problem (and a few others). The reason that it didn't work for me was that PolicyKit was disabled. There is probably a simple way to check but the way I did it was by installing boot up manager (bum) (search in the repos) and I checked that PolicyKit was ticked on it's list to start up.

Hope this helps

---

### Post by prshah on 2008-07-28
> **piyush_srivastava said:**
> 

However, since an upgrade to Hardy, all the controls in nm-applet are greyed on starting it(even the Unlock button is greyed), and I cannot 


I had [a similar problem]("http://ubuntuforums.org/showthread.php?t=844313"); but only when I run it as root. (sudo). If I run as regular user, it works fine.

---

### Post by Bealer on 2009-12-26
Came across this problem. 

Created a new user, and everything worked ok. I then copied my "home" dir files into the new user directory, and the greyed out issue came back.

Anyway did some poking, turns out it is something in the .config folder of the home directory.

Upon creating the new user, the button works fine. I can copy everything across apart from the .config folder and it still works. Once I copy the .config folder across it becomes greyed out again (after a reboot I think).

---

