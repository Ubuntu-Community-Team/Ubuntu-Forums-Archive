---
title: "Bery + XGL = No Theme."
date: 2007-04-17
forum: Desktop Effects &amp; Customization
---

### Post by Jaygo333 on 2007-04-17
Well, as you have guessed by the title, Ive tried intstalling Beryl with XGl on my computer with some success.

I did manage to install XGL and Beryl porperly. Even set up a proper GDM startup for it using the Beryl Wiki but one thing has always occured whenever I login into Ubuntu. My themes disappear the moment I start the XGL session of GDM. I change theme settings in the XGL session but the effects are not seen. If I do login into normal Gnome setting the Theme changes are visible.

I have tried following the Beryl wiki script to try and fix it with no problems. I have searched for answers on the Beryl wiki and the ubuntu wiki but with no success.

My $ gksudo gedit /usr/local/bin/startxgl.sh are as follows:

#!/bin/sh
/usr/bin/Xgl :0 -fp /usr/share/fonts/X11/misc -fullscreen -ac -accel glx:pbuffer -accel xv:fbo:0
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
sleep 4
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

#exec /etc/X11/Xsession gnome-session

Changes made to preserve the Login buttons.

---

### Post by adam.tropics on 2007-04-17
You may need to add 'gnome-settings-daemon' to your startup programs, via System-->Preferences-->Sessions

---

### Post by Jaygo333 on 2007-04-21
> **adam.tropics said:**
> You may need to add 'gnome-settings-daemon' to your startup programs, via System-->Preferences-->Sessions

Tried didnt work. Still get no themes to be displayed.
Also when I click on new Beryl theme, theres no instant change. Have to restart GDM to se changes.

---

