---
title: "Can't get desktop shortcuts to work"
date: 2013-04-16
forum: Desktop Environments
---

### Post by maulynvia on 2013-04-16
I want to use a desktop shortcut to launch a python script in a terminal window - I've tried a few approaches without success. What am I doing wrong? (using lubuntu/LXDE)

So this command launches the app successfully from the terminal:
```
python ~/Fred/poppy_friends_1/start.py
```

**Method 1**
So I create a launcher:
```
bears@bearlp:~/Fred$ cat poppyfriends-launcher.sh 
#!/bin/bash
python ~/Fred/poppy_friends_1/start.py
```

Double clicking on this produces a popup with option to 'execute' or 'execute in terminal',but clicking on either results in nothing (I did right click and make the file executable)

Creating a desktop short to the launcher as per method 2, did not work either.

**Method 2**
Create a desktop shortcut (I did right click and make the file executable):

```
~/Desktop$ cat poppys-friends.desktop 
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Exec=/home/bears/Fred/poppy_friends_1/start.py
Name=poppys-friends
```

I've tried a number of variations on this theme, but with no success.Suggestions appreciated.
M

---

### Post by seppalta on 2013-04-18
Perhaps some of the procedures listed here [http://lxlinux.com/#13](http://lxlinux.com/#13) will contain something that can help you. :)

---

