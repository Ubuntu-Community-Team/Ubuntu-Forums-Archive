---
title: "Help with GTK in OpenBox!"
date: 2008-06-30
forum: Desktop Environments
---

### Post by openBrandon on 2008-06-30
ok im not sure if this is the right place for me to post this but i need some help getting gtk to work in openbox. i searched and i couldnt find anything. any help is appreciated.

openbrandon

---

### Post by atomkarinca on 2008-06-30
Open up a terminal and type:

```
sudo apt-get install gtk-chtheme
```

after installation is finished, you can change your GTK theme using it:

```
gtk-chtheme
```

---

### Post by urukrama on 2008-06-30
There are several options. See [this]("http://urukrama.wordpress.com/openbox-guide/#Gtkthemes") for more info.

---

### Post by openBrandon on 2008-06-30
thank you guys so much for the quick responses, is there any way i can get it to use the gtk at login?

---

### Post by atomkarinca on 2008-06-30
Openbox should have that line in autostart.sh. Just check the file /etc/xdg/openbox/autostart.sh and look for the line "gnome-session-properties".

---

### Post by urukrama on 2008-06-30
> **atomkarinca said:**
> Openbox should have that line in autostart.sh. Just check the file /etc/xdg/openbox/autostart.sh and look for the line "gnome-session-properties".

Or if you don't want to use gnome-settings-daemon (so as not to mess up your gnome settings), specify the theme details in your ~/.gtkrc-2.0 file, as mentioned in the above linked to Openbox guide. Applications like gtk-chtheme or LXappearance should do this automatically when you set a theme with them.

---

### Post by eriqjaffe on 2008-06-30
FWIW, I think lxapperance is better than gtk-chtheme, since it has a preview and a couple of extra options.

---

