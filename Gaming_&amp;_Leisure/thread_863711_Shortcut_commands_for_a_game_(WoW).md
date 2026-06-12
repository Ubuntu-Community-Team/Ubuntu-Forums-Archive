---
title: "Shortcut commands for a game (WoW)"
date: 2008-07-18
forum: Gaming &amp; Leisure
---

### Post by SerpentKnights on 2008-07-18
Hello, I am wondering how I would make a shortcut to put on my desktop that would start up a terminal and execute the following command(s):

1) Open Terminal
2) Navigate to directory (in my case: /home/house/room/room
3) Open up the .exe in that last folder as following commands
     3a) ./house-world -c ../others/house.conf

Thanks in advance.

---

### Post by ad_267 on 2008-07-18
Do you need to have the terminal window open? And do you need to be in that directory?

You could right click on the desktop and select create launcher. For the command enter "/home/house/room/room/house-world -c /home/house/room/others/house.conf"

If you have to run the application from that directory then you can do this:
Go to application - accessories - terminal and enter:
```
mkdir .scripts
cd .scripts
gedit run-house-world
```
Then enter:
```
#!/bin/bash
cd /home/house/room/room
./house-world -c ../others/house.conf

```
Save that then run:
```
chmod +x run-house-world
```

Now you can right click on the desktop and select "create launcher" and for the command enter "/home/your_username_here/.scripts/run-house-world".

---

