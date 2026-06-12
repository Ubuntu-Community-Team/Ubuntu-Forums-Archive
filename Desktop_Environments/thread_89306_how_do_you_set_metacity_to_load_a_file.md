---
title: "how do you set metacity to load a file"
date: 2005-11-12
forum: Desktop Environments
---

### Post by teaker1s on 2005-11-12
my problem is I have a custom keyboard and a script that sets the keys to kernel and xmodmaps them-Ideal situation would be to get metacity to load them with each desktop as currently I can run from int.d but xmodmap is run too early so I only get key output not XF86 discription. run the script manually and its all great

---

### Post by pitr on 2005-11-12
One possible solution is to add xmodmap to gnome-session startup.  Look under System/Preferences/Sessions

---

### Post by teaker1s on 2005-11-12
thanks for the suggestion,  the problem with running as as an app it seems critical when it starts otherwise xmodmap has no effect
running it so its either 20 50 75 with update-rc.d I still get no xmodmap and I'd like one central place in metacity so as gnome or kde loads I have same effect in both with XF86 keys

---

