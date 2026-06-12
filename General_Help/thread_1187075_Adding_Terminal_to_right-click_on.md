---
title: "Adding Terminal to right-click on"
date: 2009-06-14
forum: General Help
---

### Post by kg87 on 2009-06-14
Just a quick question, 

I've been learning red hat due to work, and noticed you could launch terminal from right clicking the desktop (selecting from the menu). Is this available in ubuntu?

Thanks

---

### Post by mdurham on 2009-06-14
> **kg87 said:**
> Just a quick question, 

I've been learning red hat due to work, and noticed you could launch terminal from right clicking the desktop (selecting from the menu). Is this available in ubuntu?

Thanks

Yes it is. Just install 'nautilus-open-terminal' with Synaptic. You can then open a terminal in any directory selected with Nautilus.

---

### Post by kg87 on 2009-06-14
hmm, That doesnt seem to be the solution. Im looking to add an icon to the right click menu, so it will allow the launch of a seperate terminal (ie same menu as "change background")

---

### Post by Legace on 2009-06-14
Type in the following in Terminal:
```
sudo mkdir ~/.gnome2/nautilus-scripts
```

Then browse to **~/.gnome2/nautilus-scripts** with Nautilus:
```
nautilus ~/.gnome2/nautilus-scripts
```

And create a new file in that directory, for example **terminal**

Open that newly created file with Text Editor (gedit) and enter the following text:
```
#!/bin/bash
# Open Gnome-terminal
exec gnome-terminal
```

Save the file and close gedit.

Type in (note, replace firefox with whatever you entered above:
```
sudo chmod 755 ~/.gnome2/nautilus-scripts/terminal
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

### Post by AndyCee on 2009-06-14
*Yes it is. Just install 'nautilus-open-terminal' with Synaptic. You can then open a terminal in any directory selected with Nautilus.*

> **kg87 said:**
> hmm, That doesnt seem to be the solution. Im looking to add an icon to the right click menu, so it will allow the launch of a seperate terminal (ie same menu as "change background")

Nautilus is the file-browser in Ubuntu. When you install "nautilus-open-terminal", you right-click, and get "Open Terminal" option. You have to restart nautilus to see it happen (log out or "killall nautilus").

I think "nautilus-actions" has this function too.

Isn't that what you're looking for?

---

### Post by kg87 on 2009-06-14
legace's method worked. It was actually overkill, but broadened my horizions, presumably i can generate more scripts add em to that menu, spot on cheers guys,

Andycee, however valid you suggestion may be, that required nautilus "filebrowser" to be open. I just wanted to be able to launch it directly from desktop. :D

---

### Post by AndyCee on 2009-06-14
> **kg87 said:**
> legace's method worked. It was actually overkill, but broadened my horizions, presumably i can generate more scripts add em to that menu, spot on cheers guys,

Andycee, however valid you suggestion may be, that required nautilus "filebrowser" to be open. I just wanted to be able to launch it directly from desktop. :D

It works on my desktop too, I just didn't want to broadcast several personal items from my desktop on the interweb :D.

Not that there's anything wrong with doing the nuts & bolts way. I've learnt something new today too.

EDIT: Question - does anyone know what happened to the "thanks" button?

---

### Post by nandemonai on 2009-06-14
You need to re-log in order for the nautilus terminal plugin to become active.

---

