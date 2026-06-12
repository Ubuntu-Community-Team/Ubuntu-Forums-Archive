---
title: "Login screen won't load."
date: 2009-04-14
forum: General Help
---

### Post by Alyn on 2009-04-14
OK, I changed my login screen for [this one]("http://www.gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883") from gnome-look.org.  Now I have a big problem, when I turn my computer on, it won't load, I just get the timer icon for ages and ages and ages, which means I can't login, which means I can't change it, so I'm effectively locked out of my computer.

---

### Post by nothingspecial on 2009-04-14
The fix is in the comments below the theme in your link. If you are unsure of it post back.

Make sure you type the line ```
sudo rm -rf /usr/share/gdm/themes/nUbuntu
```
exactly right. Do not leave a space after / whatever you do. This will completely delete everything from your computer, all files, Ubuntu itself. Like I said if you are unsure post back before you do anything.

---

### Post by Alyn on 2009-04-14
I feel stupid for not having noticed that.  However, I have tried it and it has apparently made no difference at all. I still can't log in.  Is there a way to log in from the command line?

---

### Post by nothingspecial on 2009-04-14
When you boot up it will say something like 
```

grub loading
press esc for menu
```

Press escape and you will get the option to boot into a shell.

Did you try the fix further down the page?

---

### Post by Alyn on 2009-04-14
Ok, fixed, this worked:

> $ sudo nano /etc/gdm/gdm.conf-custom
search for "nUbuntu", replace it by "Human" as this is the default theme for Ubuntu 8.04

Thank you so much for the help, feel stupid that the answer was staring me in the face to begin with :P

---

### Post by nothingspecial on 2009-04-14
Nice one :guitar:

---

