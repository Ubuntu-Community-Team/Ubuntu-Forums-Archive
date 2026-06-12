---
title: "gksu / gksudo asking to remember password"
date: 2009-04-28
forum: General Help
---

### Post by wesgarner on 2009-04-28
I was redoing my permissions for my home folder. After, every time I run a gksu it requests to remember the password (gksudo does not)
I want to prevent it from saving the password or asking to remember it

What do I need to change?

---

### Post by Nepherte on 2009-04-28
You have to add timestamp_timeout to /etc/sudoers: [http://ubuntuforums.org/showpost.php?p=4767816&postcount=5](http://ubuntuforums.org/showpost.php?p=4767816&postcount=5)

If you're having problems with vi as editor, try this:
```
sudo EDITOR=nano visudo
```

---

### Post by wesgarner on 2009-04-28
The sudo timeout isn't the problem - I don't mind the timeout. I just don't want it to request remembering the password when I run Synaptic or other sudo-required app

gksu - has checkbox to remember password
gksu does not

---

### Post by sisco311 on 2009-04-28
I'm not sure, but I think you can change the settings in gconf-editor.

```
gksu gconf-editor
```

and set /app/gksu/save-to-keyring to false and set it Mandatory. 

If it doesn't work Unset the key from File -> New Mandatory Window.

---

