---
title: "Sudo Apps Look Gray?"
date: 2006-03-07
forum: Desktop Environments
---

### Post by Coolit on 2006-03-07
This isn't really that much of an issue but here goes... 

When I launch an app using sudo the apps Gui's appear to look Gray and default, this only happens when I run them as the super user, is there a way to force them to look the same as the Gnome theme my user account is using? Synaptic looks terrible! :(

Thanks for any replies :-)

---

### Post by pbaehr on 2006-03-07
I don't know if this has anything to do with the grey issue but if you are manually launching the apps from the command line you should always use gksudo rather than plain ol' sudo when you're launching a graphical application.

---

### Post by frodon on 2006-03-07
[QUOTE=Coolit]This isn't really that much of an issue but here goes... 

When I launch an app using sudo the apps Gui's appear to look Gray and default, this only happens when I run them as the super user, is there a way to force them to look the same as the Gnome theme my user account is using? Synaptic looks terrible! :(

Thanks for any replies :-)[/QUOTE]It's because sudo apps use a default (ugly) theme and not your current theme.
To avoid that : [http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_CHANGE_GTK_THEMES_FOR_ROOT_APPLICATIONS_.26_GTK_GREETER](http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_CHANGE_GTK_THEMES_FOR_ROOT_APPLICATIONS_.26_GTK_GREETER)

---

### Post by nocturn on 2006-03-07
The simple solution.

Install themes/icons etc in /usr/share/themes and /usr/share/icons instead of .themes and .icons in your home directory.

That way, your root apps will follow both your GTK and icon settings.

---

### Post by adamkane on 2006-03-07
Apply your favorite theme, then copy the files from home to root.

```

sudo ln -s /home/<insert your username here>/.themes /root/.themes 
sudo ln -s /home/<insert your username here>/.icons /root/.icons 
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

```
[http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_CHANGE_GTK_THEMES_FOR_ROOT_APPLICATIONS_.26_GTK_GREETER](http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_CHANGE_GTK_THEMES_FOR_ROOT_APPLICATIONS_.26_GTK_GREETER)

---

### Post by nocturn on 2006-03-07
[QUOTE=adamkane]Apply your favorite theme, then copy the files from home to root.

```

sudo ln -s /home/<insert your username here>/.themes /root/.themes 
sudo ln -s /home/<insert your username here>/.icons /root/.icons 
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

```
[http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_CHANGE_GTK_THEMES_FOR_ROOT_APPLICATIONS_.26_GTK_GREETER](http://doc.gwos.org/index.php/Desktop_EyeCandy#HOWTO:_CHANGE_GTK_THEMES_FOR_ROOT_APPLICATIONS_.26_GTK_GREETER)[/QUOTE]

The advantage of putting them in /usr/share/themes is that they are available to all users on the system.  Updates go to everyone etc.

---

### Post by Coolit on 2006-03-07
Thanks for the help, it's looking great now :-)

---

