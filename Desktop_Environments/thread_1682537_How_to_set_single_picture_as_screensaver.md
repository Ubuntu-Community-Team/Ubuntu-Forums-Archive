---
title: "How to set single picture as screensaver?"
date: 2011-02-06
forum: Desktop Environments
---

### Post by RuneLacroix on 2011-02-06
Hey Forum.

I want to have a single picture as screensaver.

The Gnome-screensaver seems to be in sufficient so I installed xscreensaver, but cant figure how to set a single picture as screensaver there.

Also most help threads on the topic is dated 2006 or 7, and arent to much help anymore.

Can anyone help me?

Kind Regards, Rune

---

### Post by ajgreeny on 2011-02-06
Interesting question, but why just one picture?  If you can move all your pictures to a folder called My-Pictures and put your required picture in the normal Pictures folder in home, you could use the Pictures Folder screen saver.

It used to be possible to change the folder used for that screen saver, but I'm not sure if you can do that any more.  Edit the /usr/share/applications/screensavers/personal-slideshow.desktop  file with gksudo gedit to point to the folder of your choice with the one picture in it.

Edit the Pictures folder configuration file:
Code:

sudo gedit /usr/share/applications/screensavers/personal-slideshow.desktop

Find the line
Code:

Exec=slideshow --location=Pictures
In Hardy Heron, the line is simply "exec=slideshow." To customize the location, just add "--location=PATH," where PATH is the location of your pictures.

and change it to
Code:

Exec=slideshow --location=/path/to/your/Pictures_folder

---

### Post by RuneLacroix on 2011-02-06
Thanks for the reply.

In 10.10 it looks like this
```
[Desktop Entry]
Name=Pictures folder
Comment=Display a slideshow from your Pictures folder
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver
```

And i couldn't figure out how to change it to a custom folder... Well... i found a easy way. Using the Fspot screensaver in gnome-screensaver, and just only adding one picture to the source in fspot.

---

