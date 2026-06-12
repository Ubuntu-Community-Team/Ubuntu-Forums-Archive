---
title: "Keyboard does not work in unity/gnome shell. Works in LightDM"
date: 2011-12-23
forum: Desktop Environments
---

### Post by anch0 on 2011-12-23
I have an updated ubuntu system, one week old about the updates. I cannot work anymore with it, I installed a gnome extension (instructions [here]("http://www.webupd8.org/2011/06/soundmenu-like-gnome-shell-extension.html")) and after that I restarted the shell (alt+F2 then r).
With the login screen the keyboard works, and I can switch to a tty too. But after login to any desktop enviroment (gnome shell, unity, gnome classic) the keyboard does not work, not even the leds of num lock neither caps lock. What can I do? How can I force to redetect my keyboard? There is a automated script that can do that? The mouse is working fine. Both the keyboard and the mouse are ps/2.

---

### Post by BC59 on 2011-12-23
If you go to System Settings--Keyboard Layout you can play a little bit to see if there is a difference.

---

### Post by BC59 on 2011-12-23
I found this, I don't know if you already did it:

install scim-bridge

```
sudo apt-get install scim-bridge
```

edit /etc/X11/xinit/xinput.d/scim as root

```
sudo gedit /etc/X11/xinit/xinput.d/scim
```

Find the line 

> GTK_IM_MODULE and change it into GTK_IM_MODULE="scim-bridge"

then save and reboot

---

### Post by anch0 on 2011-12-23
> **BC59 said:**
> I found this, I don't know if you already did it:

install scim-bridge

```
sudo apt-get install scim-bridge
```

edit /etc/X11/xinit/xinput.d/scim as root

```
sudo gedit /etc/X11/xinit/xinput.d/scim
```

Find the line 



then save and reboot

That didn't work.. I'll install xfce4 to give a try..

---

### Post by anch0 on 2011-12-23
After installing xfce4, the keyboard works but only in this Xfce Desktop Environment. 
With Unity, Gnome3 and Gnome classic still I have this problem.
What does those desktops environment have in commmon that causes the keyboard stop working or crash and xfce4 don't have?

---

### Post by anch0 on 2011-12-28
If I start session as a guest, keyboard works with Unity, Gnome Shell and Classic.. so it has to be with something in my session. What should I erase? there is a hidden folder in /home that maybe is corrupted?

---

### Post by anch0 on 2012-01-06
The keyboard also works with KDE with my default user, not a guess user. Definitely something is corrupted with the gnome/unity desktop only. help

---

### Post by anch0 on 2012-03-23
*bump

---

### Post by apaan on 2012-12-12
Got the same problem after installing 12.10 (not upgrading, but installing from scratch). Before login, the keyboard is working, but after login it isn't.

Did your problem eventually solved? What was the solution?

---

