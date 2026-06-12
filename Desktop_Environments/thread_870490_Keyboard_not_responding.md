---
title: "Keyboard not responding"
date: 2008-07-25
forum: Desktop Environments
---

### Post by mosestruong on 2008-07-25
I'm having an intermittent problem with the keyboard. It seems as though it is not focusing on a window, hence the keyboard input is not captured by the window.

This seems to happen if I have a terminal window, then Alt-tab to Firefox, and then Alt-tab back, the terminal no longer responds... I can alt-tab out of it, but in order for terminal to respond to the keyboard, I need to use the mouse to bring the terminal back into focus again.

This also affects Kate, in which case, after saving the Kate no longer respond to the keyboard, but need to alt-tab out of it and then use the mouse to give focus back to it.

Does anyone know how to fix this? thanks

---

### Post by dxahz on 2008-10-10
I have the same problem for kate, using ubuntu 8.04, must switch window to re-enable keyboard input again, quite annoying:-(, this is the only thing that I don't like for ubuntu

---

### Post by dxahz on 2008-11-09
This seems to be a solution:

1. sudo apt-get install scim-bridge-client-qt

2. Edit the file /etc/X11/xinit/xinput.d/scim by typing in a terminal (Applications>Accessories>Terminal): 

sudo gedit /etc/X11/xinit/xinput.d/scim

Change the line:

GTK_IM_MODULE=xim

into :

GTK_IM_MODULE="scim-bridge"

Change the line:

QT_IM_MODULE=xim

into :

QT_IM_MODULE="scim-bridge"

---

### Post by prosist on 2012-05-15
thanks, that worked for me.
it was really driving me crazy

---

### Post by oldos2er on 2012-05-15
Old thread closed.

---

