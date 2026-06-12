---
title: "i lost the tops to my windows!!!!"
date: 2007-06-16
forum: Desktop Effects &amp; Customization
---

### Post by Rufi0h on 2007-06-16
somehow when i make Beryl my window manager I lose the tops to my windows. i cant move them or close them. any suggestions on what i can do to fix this?

here is a link to the picture
[http://img378.imageshack.us/img378/9012/screenshotyo9.png](http://img378.imageshack.us/img378/9012/screenshotyo9.png)

---

### Post by andrewsomething on 2007-06-16
Right click on the Beryl icon in your system try and select a window decorater. You might have to install Emerald, which is Beryl's default window decorater if you don't already have it.

---

### Post by luisromangz on 2007-06-16
If you are using the nvidia closed source driver, you need to add 

AddRGBGLXVisuals "true"

to your Display (or device I don't remember) section in xorg.conf.

Bye!

---

### Post by Rufi0h on 2007-06-16
i forgot to mention i am a super noob, so please tell me how to add the code into xorg.conf

---

### Post by finer recliner on 2007-06-16
EDIT: i always recommend backing up important system files before editing them:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bck

```

to edit your xorg.conf, type this in a terminal:
```

gksudo gedit /etc/X11/xorg.conf

```

you will be prompted for your password.

after editing xorg.conf file, you need to restart X to see the changes. this can be done with ctrl+alt+backspace (you will be logged out) or just restart the computer.

---

### Post by Rufi0h on 2007-06-21
lets say i might of messed up the config, how do i get to the back up which i made.

---

### Post by freshmeatz on 2007-06-21
open up beryl manager , go to profiles , click default, if you didnt make a seperate profile before you started to edit the default one, you can allways go back thru each setting and click the box to the left of the setting in question to reset that one settting to default:(

user beryl settings should be found in /home/username/.beryl

---

### Post by Ultra Magnus on 2007-06-21
This happened to me when I first installed beryl - for me the problem was that I installed beryl but not beryl manager. If this is whats happened then try getting beryl manager

sudo apt-get install beryl-manager

After that select a theme from the emerald theme manager: system -> preferences -> emerald theme manager

Hopefully you should have the tops of your windows back!

---

