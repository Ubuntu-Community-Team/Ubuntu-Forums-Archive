---
title: "Program visible in menu but can not find in &quot;application menu&quot; list"
date: 2013-05-14
forum: Desktop Environments
---

### Post by GumpTron on 2013-05-14
Thank you for helping.

I decided to install xubuntu and use the xfce option. I am darn happy with it :)

thing is, under the menu and the "internet" section I can see a link to a program I no longer use and have removed all traces of from my home folder. When i click it it says " Failed to execute command "/home/blech/firestorm/etc/../firestorm". (no such file or directory) 

Now this makese sense because I removed it. Thing is I want to remove this from the menu. So, i right clicked the menu tab and chose "properties" then "menu file" and then "edit menu". I then navigated to "internet" but the links are not present thus i cant remove them. I am not sure what else to do and would appreciate any help. Thank you..

---

### Post by Toz on 2013-05-14
How did you install the program? Since its in your home directory, was it something you downloaded and extracted into your home directory?

Have a look for a .desktop file in /home/blech/.local/share/applications that is related to firestorm.

---

### Post by ibjsb4 on 2013-05-14
Also look in /usr/share/applications

---

### Post by dentaku65 on 2013-05-14
Also you can try
```
sudo updatedb
locate firestorm
```

---

### Post by GumpTron on 2013-05-15
ty worked :)

---

### Post by ibjsb4 on 2013-05-15
Don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by GumpTron on 2013-05-17
done :)

ty

---

