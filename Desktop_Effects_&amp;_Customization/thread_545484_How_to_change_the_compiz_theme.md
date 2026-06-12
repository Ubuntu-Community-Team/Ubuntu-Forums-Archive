---
title: "How to change the compiz theme"
date: 2007-09-07
forum: Desktop Effects &amp; Customization
---

### Post by damarius on 2007-09-07
I'm new to Ubuntu and I've been trying for a while to modify the compiz theme.
I would like to change the window decoration for instance.
The nvidia driver is all good to go and the Desktop Effects are enabled and working but I can't seem to find a command or application that changes the window decoration for compiz
I've been trying to find an answers on this forums but all these things with beryl and compiz and compiz fusion and emerald and gtk-window-decorator generated only confusion.
so if anyone could just tell me how to install a cgwdtheme for example I'd be more than grateful.

---

### Post by Inxsible on 2007-09-07
If you do not use emerald, you need to use gnome-compiz-themer and you can simply drag and drop your cgwd file into it.

---

### Post by damarius on 2007-09-07
this may be a stupid question, but do I have to download the themer ?
And, if so, could you provide a link ?
Thanks

---

### Post by Inxsible on 2007-09-07
yes open a terminal and type in ```
sudo apt-get install gnome-compiz-manager
```

---

### Post by damarius on 2007-09-07
I installed this application before but I can't just drag and drop the cgwdtheme file on the application.
There are settings that refer to effects and other things but nothing about window decoration

---

### Post by 1337455 10534 on 2007-09-10
How can I use emerald to change a theme?? I found a nice one but it does not switch to it.

---

### Post by ryno519 on 2007-09-10
> **1337455 10534 said:**
> How can I use emerald to change a theme?? I found a nice one but it does not switch to it.

You could start compiz like this

```
compiz --replace -c emerald &
```

and then use the Emerald Theme Manager in your preferences menu to select your theme. :)

---

### Post by waddletron on 2007-09-15
> **Inxsible said:**
> yes open a terminal and type in ```
sudo apt-get install gnome-compiz-manager
```

And then what?

```
luser@C2D-desktop:~$ sudo apt-get install gnome-compiz-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-compiz-manager is already the newest version.

```

```
luser@C2D-desktop:~$ gnome-compiz-manager
bash: gnome-compiz-manager: command not found

```

---

### Post by waddletron on 2007-09-19
> **ryno519 said:**
> You could start compiz like this

```
compiz --replace -c emerald &
```

and then use the Emerald Theme Manager in your preferences menu to select your theme. :)

Guess again.

luser@C2D-desktop:~$ /usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: Couldn't load plugin '-c'
/usr/bin/compiz.real: Couldn't load plugin 'emerald'
/usr/bin/compiz.real: 'decoration' plugin must be loaded before 'scale' plugin
/usr/bin/compiz.real: Can't activate 'decoration' plugin due to dependency problems

---

### Post by 1337455 10534 on 2007-09-28
is running ccsm not working? ok;
the prblm with emerald was solved by using a theme as a template for making a custon one, and then saving the custom.

---

