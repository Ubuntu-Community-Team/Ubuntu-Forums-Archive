---
title: "keyboard doesn't function properly"
date: 2010-02-15
forum: Desktop Environments
---

### Post by iriswortman on 2010-02-15
My daughter (3) tried playing on my laptop for the first time today, and now my keyboard doesn't function properly anymore. I get really strange thing, for example, when I type the letter 'e' in stead of an e there's urwe=q , when hitting caps I get '65' something in stead. Other keys do not function at all, some numbers, some letters as well. I do not know what to do anymore. It's not my num lock, its not caps. Anyone know what to do? I have Ubuntu 9.04 (thoug I'm using my husbands computer with vista now becouse I cannot type anymore on my own ) Ooooo I feel so stupid.

---

### Post by warp99 on 2010-02-15
In the menu go under System > Preferences > Keyboard > Layouts and make sure edev is choosing the correct keyboard for your laptop.

---

### Post by iriswortman on 2010-02-17
unfortunately that doesn't seem to work either at the moment: I chose two types of layouts, 
 
e   =    urwe=q , e= or [e=q] or [e=urw] or e]u[ or e=][urw
c   =    c= or c='j or c=mvx
3   =    3=
8   =    87
 
 
keys that do not function at all are
 
a,s,d,q,5,6,0
 
I just don't get it.
 
Anybody?

---

### Post by warp99 on 2010-02-17
Does the keyboard function correctly at the command prompt when you use ctrl+alt+f1 to switch to a terminal? If so then create a new user with admin rights and login with that user. Here's a quick guide on doing this:

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

It may be that your daughter changed some settings by accident.

Edit: To get back to your desktop from the terminal press ctrl+alt+f7

---

### Post by iriswortman on 2010-02-17
no still no luck. even when I'm typing in the terminal I do not get normal letters. do you have any other suggestions? I even tried reïnstalling Ubuntu, but even after a reïnstall it still has the same problem
 
thank you for all your suggestions already

---

### Post by warp99 on 2010-02-17
This seems like a hardware issue since a re-install would have wiped out your /home directory and any personal settings since nothing is retained.

Does it do this when you boot to a Ubuntu LiveCD or even another distro's LiveCD?

---

### Post by iriswortman on 2010-02-18
I tried both installing Ubuntu 9.04 from disk and XP from disk. XP didn't install at all, some error which I can't remember anymore. Maybe the thing is just beyond repair.

---

### Post by mcduck on 2010-02-18
What didi youa ctuallt try to change in /system/Preferences/Keybaord? You need to make sure that A) the language is correct, and B) the keybaord model is correct.

If you can't find the exact model then use one of the Geeneric models, but make sure you choose one that has the correct amount of keys for your keybaord.

Trying to use a layout with wrong number of keys is the most common reason for keys not working or giving wrong letters.

---

### Post by warp99 on 2010-02-18
> **iriswortman said:**
> I tried both installing Ubuntu 9.04 from disk and XP from disk. XP didn't install at all, some error which I can't remember anymore. Maybe the thing is just beyond repair.

Looks like a hardware issue. I would suggest downloading a diagnostic CD to check you system. Ultimate Boot CD has a ton of tools to check your system:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

BTW don't keep installing the OS, it's a waste of time and effort. You're already running a complete operating system when using a Ubuntu LiveCD. You need to figure out what's the problem with the hardware first. When that's resolved do an install be it Ubuntu or Windows or both.

---

