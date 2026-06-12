---
title: "Wierd menu bar"
date: 2007-07-27
forum: Desktop Environments
---

### Post by yun4 on 2007-07-27
I'm not too sure if I made it so but my menu bar keeps appearing at the top left corner and i was wondering if anyone can teach me how to change it back? Here is a SS of what it looks like

[http://img527.imageshack.us/my.php?image=screenshotnz8.png](http://img527.imageshack.us/my.php?image=screenshotnz8.png)

---

### Post by ayoli on 2007-07-27
looks like you have tried a patched gtk to have mac menu bar.
Now you have 3 solutions:
1. you use the mac menu applet to have the menu in your top panel. look [here]("http://ubuntuforums.org/showthread.php?t=241868")

OR

2. you edit/create a .gnomerc ile in your home (don't forget the leading dot) like this
```
gedit ~/.gnomerc
```
and put in it:
```
export GTK_MENUBAR_NO_MAC=1
```
this desactivates mac menu

OR

3. you reinstall original gtk packages to get completly rid of patched gtk like this:
```
sudo apt-get install libgtk2.0-0 --reinstall
```

use one of these 3 ways

---

### Post by yun4 on 2007-07-31
wow thanks for the help, works perfectly now. thank you

---

