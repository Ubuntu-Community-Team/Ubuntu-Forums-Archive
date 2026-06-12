---
title: "All the top bar and Activity bar icons dissapeared on Gnome 3.10"
date: 2014-07-05
forum: Desktop Environments
---

### Post by nikola8 on 2014-07-05
Hello,


After last updates on ubuntugnome 13.10, I get this bug, almost everything if not everything dissapear from the top bar. Also when I press the super button and want to open a program  I can see neither the letters nor the program's icon and when I am on lock screen and try to log in I can't see any letter of the username or the buttons. Here are pictures of what exactly is going on becuase I am not sure I can explain it well enough.


  
Thanks

  [URL="http://i.stack.imgur.com/TrB3v.png"]
http://i.stack.imgur.com/TrB3v.png[/URL]  [http://i.stack.imgur.com/tqdM4.png](http://i.stack.imgur.com/tqdM4.png)

---

### Post by mooreted on 2014-07-06
Try deleting .gnome and .gnome2 folders then log out and back in. That should reset all the settings to Gnome defaults.

---

### Post by nikola8 on 2014-07-07
didn't find those folders anywhere, just .gconf which I deleted but It didn't do anything. The whole thing is strange because when I restart the laptop everything is OK and after certain amount of time everything just vanishes.. No unusual activity or any warning message.

---

### Post by mooreted on 2014-07-07
I'm not running Gnome, so I'm working from memory here. Maybe look in .config, there might be gnome config folders in there.

Do you have any trouble creating files and folders on your laptop? It could be your user profile is having problems or there could be a problem with your hard drive, or permission problems for the files and folders in your directory.

One thing you could try is to create a new user and log in as that user to see if it's a problem related to your user profile.

---

### Post by nikola8 on 2014-07-07
@mooreted 
After creating a new user the problem seems to be solved, will see if I set up everything again like the previous user, how it will behave. Thanks

---

### Post by mooreted on 2014-07-07
You are welcome, good luck.

---

### Post by nikola8 on 2014-07-09
I found it .. the extension BackSlide caused all the troubles..

---

