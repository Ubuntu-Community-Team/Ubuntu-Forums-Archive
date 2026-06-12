---
title: "Modify Gnome Right Click Options"
date: 2009-06-06
forum: General Help
---

### Post by Jaded Misanthrope on 2009-06-06
I would like to modify the right-click menu that appears on the Gnome Desktop to contain, among other things, submenus containing shortcuts to various applications (e.g. Firefox and the terminal). How would I go about doing this on Ubuntu 8.10? It seems simple, but a quick Google didn't return anything relevant.

---

### Post by Legace on 2009-06-06
Type in the following in Terminal:
```
sudo mkdir ~/.gnome2/nautilus-scripts
```

Then browse to **~/.gnome2/nautilus-scripts** with Nautilus:
```
nautilus ~/.gnome2/nautilus-scripts
```

And create a new file, for example **firefox**

Open that newly created file with Text Editor (gedit) and enter the following text:
```
#!/bin/bash
# Open Gnome-terminal
exec /usr/bin/firefox
```

Save the file and close gedit.

Type in (note, replace firefox with whatever you entered above:
```
sudo chmod 755 ~/.gnome2/nautilus-scripts/firefox
```

Reboot, and it should work :)
Or alternatively, type in to restart Nautilus (replace *pid_of_nautilus* with the Nautilus process ID, which can be found in System Monitor):
```
kill -HUP *pid_of_nautilus*
```

---
Note, to get the location of an app, like **/usr/bin/firefox** for Firefox, you can use the whereis command. For example:
```
whereis firefox
```

:)

---

### Post by Jaded Misanthrope on 2009-06-06
That's a start, certainly, but it'd be kind of nice to be able to modify the contents of the desktop right-click slightly more, e.g. removing the 'create directory / file' options, having some of the shortcuts outside their own submenu and having more submenus with configurable names. I'm probably overlooking something really obvious here, though. :|

---

