---
title: "Compiz Fusion or Beryl on Feisty Fawn?"
date: 2007-07-09
forum: Desktop Effects &amp; Customization
---

### Post by dmee on 2007-07-09
Hey guys, may be my question is pretty worn but anyway: I'm gonna install Feisty Fawn on my laptop with ATI videocard. The question is: what will you advice to install -- brand new Compiz Fusion or Beryl to get super cool visual effects on the one hand and pretty solid system on the other hand?

Btw, what's better -- XGL or AIGLX?

Thank you.

Dmitry

---

### Post by koshari on 2007-07-09
to begin wiht is your ati card better than 9500/x300?

as for beryl versus fision, you may as well go with fusion as beryl wont be developed any more.

---

### Post by dmee on 2007-07-09
I have the X1400 card.

---

### Post by edwin.e.johnson on 2007-07-09
fusion is way to buggy go with beryl i have had both and fusion is getting much better but beryl is much more stable at this time....

try this



how to install beryl on ATI



------------------------------------------------


make sure your system is updated.

system>admin>update manager

-------------------------------------

activate restricted drivers

System>Administration>Restricted Drivers Manager

and enable your ATI driver.


NOW REBOOT


---------------------------------------

INSTALL XGL.


Code:

sudo apt-get install xserver-xgl

-----------------------------------------

XGL won't load on its own so we need to write a few scripts to have it start.

Code:

sudo gedit /usr/local/bin/startxgl.sh

-------------------------------------

put this in your startxgl.sh file

Code:


#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session



now save and make the script executable

------------------------------------------

Code:

sudo chmod a+x /usr/local/bin/startxgl.sh



Now we need to create a way to login and launch that

-----------------------------------------------------

Code:

sudo gedit /usr/share/xsessions/xgl.desktop

put this test into that file

-----------------------------------------------------

Code:

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application





now make that script executable

------------------------------------------------------------------

Code:

sudo chmod a+x /usr/share/xsessions/xgl.desktop

NOW LOG OUT  <ctrl><alt><backspace> and click "sessions on you logon screen...... select """gnome with xgl""""


-----------------------------------

NOW TO ADD BERYL

-------------------------------------

Code:

System> Administration> Software sources

now disable the universe repo and hit close and reload.
Now we need to add the beryl repo.

-----------------------------------------

install the repo key

Code:

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -


--------------------------------------------------
Now add this source to your Software sources via the Third party tab

System> Administration> Software sources

Code:

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main

hit close and reload


--------------------------------
Code:

sudo apt-get install beryl emerald-themes

Once that's finished installing you can launch beryl with


Code:

beryl-manager

or go to 

system>preferences>sessions>

click "NEW"

for the name and the command put,

beryl-manager

this will have beryl load at startup

---

### Post by hyperair on 2007-07-09
Rule of thumb: AIGLX is always better, but if you really have no other choice then fall back to XGL.

---

