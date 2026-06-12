---
title: "How can i change the login window?"
date: 2010-02-10
forum: Desktop Environments
---

### Post by shinrry on 2010-02-10
[FONT=Comic Sans MS][SIZE=3]hi, i am currently using Ubuntu 9.10. How can i change the appearance of the window in which i input my user name and password when i login?
Actually i have download a theme from [http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter), but it seems invalid.[/SIZE][/FONT]

---

### Post by Pritamsng on 2010-02-10
[COLOR=#51555c]**Go to ....System->Administration** -> **Login Window. you can change the loin screen,**[/COLOR]

---

### Post by sisco311 on 2010-02-10
Try this python script: [thread=1358026]GDM2 Configuration Tool[/thread]

or run the theme manager as user gdm:
```
sudo -u gdm dbus-launch gnome-appearance-properties
```
or set the theme in gconf editor:
```
sudo -u gdm dbus-launch gconf-editor
```
edit the value of the /desktop/gnome/interface/gtk_theme key

---

### Post by Baneblade on 2010-02-10
> **Pritamsng said:**
> [COLOR=#51555c]**Go to ....System->Administration** -> **Login Window. you can change the loin screen,**[/COLOR]

That is no longer true for 9.10 I'm afraid. Due to a new GDM older themes and config utilities are no longer compatible. 

Far as I know you should still be able to change the background image for the login (they are found here: /usr/share/images/xsplash)

OP, you may want to have a look at this thread, as I think its what you were after? [http://ubuntuforums.org/showthread.php?t=1333683]("http://ubuntuforums.org/showthread.php?t=1333683")

---

### Post by Pritamsng on 2010-02-10
thanks bro... its really gr8... it undoubtly solved my much more doubt...

---

