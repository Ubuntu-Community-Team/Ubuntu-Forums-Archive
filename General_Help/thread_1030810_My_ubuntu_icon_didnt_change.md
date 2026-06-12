---
title: "My ubuntu icon didnt change"
date: 2009-01-04
forum: General Help
---

### Post by Secret Neo on 2009-01-04
i tried to change my icon on the panel by going thru the conf and changing the path of the 'custom icon" but nothing helped. i even tried killall gnome-panel but its still the same. and i cant access the folder the original logo is in cuz my permission is denied. ideas?

---

### Post by matteojg on 2009-01-05
This might be of help: [https://answers.launchpad.net/ubuntu/+question/14834](https://answers.launchpad.net/ubuntu/+question/14834)

---

### Post by mcduck on 2009-01-05
That setting only works for the "Drawer" applet and the "Main menu"-applet. Main menu is the win9x-style single-button menu.

If you are trying to change the distributor logo while using the "Menu bar"-applet (the one with three buttons, Application/Places/System), you need to do it by replacing the actual icon file in the icon theme you are using.

---

### Post by chamber on 2009-01-05
You can also do it by installing ubuntu tweak.

Edit your sources.list file
```

gksudo gedit /etc/apt/sources.list

```
add the following line
```

http://ppa.launchpad.net/tualatrix/ubuntu hardy main

```
update
```

sudo apt-get update 

```
then
```

sudo apt-get install ubuntu-tweak 

```

---

