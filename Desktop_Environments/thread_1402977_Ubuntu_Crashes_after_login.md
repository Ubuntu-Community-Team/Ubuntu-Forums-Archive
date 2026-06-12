---
title: "Ubuntu Crashes after login"
date: 2010-02-09
forum: Desktop Environments
---

### Post by Brightneon_Latte on 2010-02-09
Hello:
I was adding compiz effects in compiz manager when after I selected the window effect (one with a picture of a window with light reflection on it) and then suddenly my computer crashed. I turned it off, turned it on, logged in and after the starting sound, ubuntu won't load. Any suggestions on how to solve it?
I'm using Karmic Koala.

---

### Post by Brightneon_Latte on 2010-02-09
Any help???
I want to use my ubuntu again :(

---

### Post by Brightneon_Latte on 2010-02-09
Solved it! hard to say it, but with no support from here...

For the ones that may have this problem


[LIST]
[*]Start your computer
[*]Enter safe mode
[*]When a menu appears, using the keypad, move to the last option (run prompt shell with networking)
[*]In there, log in with your information
[*]After logging in, write the next codes
[/LIST]
```
sudo apt-get remove compiz
```
```
sudo apt-get remove compiz-core
```
```
exit
```

this will remove compiz and stop your system from crashing, and turn it off.


[LIST]
[*]Turn it on and you will log-in as normal
[*]Now, go to synaptic and install compiz
[*]that's it
[/LIST]
Note: this time, don't apply the effects that damaged your computer the first time.

Hope this helps for future reference!!

---

