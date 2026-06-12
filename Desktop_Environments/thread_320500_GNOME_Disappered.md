---
title: "GNOME Disappered"
date: 2006-12-17
forum: Desktop Environments
---

### Post by lakelovers on 2006-12-17
I lost my audio a few days ago and in my effort to restore the audio I managed to alienate GNOME. It refuses to show it's face. What do I do? KDE works find, that's what I get on login. I tried to change the desktop to "default" but KDE comes up. Here's hoping somebody out there can lead me back to GNOME.

Jerry

---

### Post by taurus on 2006-12-17
From a terminal, run

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```
Now, see if you can log into Gnome from the GUI login screen!

---

### Post by lakelovers on 2006-12-17
Thanks. . . I reinstalled a bunch of GNOME things I apparently removed during my messing around with the audio stuff. I think a new Murphy's law might be: if things are going along quite smoothly, something will throw a wrench in the cogs. I really like Ubuntu, though occationally, something happens to make me climb the wall. It's not just Ubuntu, Every OS I've used has take a swipe at me.
Jerry

---

### Post by taurus on 2006-12-17
Or the second condition of Murphy's law is if things work great, don't screw with them...  ;)

---

### Post by kanna1620 on 2007-01-15
> **taurus said:**
> From a terminal, run

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```
Now, see if you can log into Gnome from the GUI login screen!

I have installed the ubuntu-desktop.And kde-desktop after installing the ubuntu-desktop.Now I lost the default desktop manager to kdm the gdm doesnt remain the default desktop manager anymore How to make it the default desktop manager? I tried
```
 sudo /etc/init.d/gdm start
``` but it didnt work

---

### Post by obsidion on 2007-01-15
> **kanna1620 said:**
> I have installed the ubuntu-desktop.And kde-desktop after installing the ubuntu-desktop.Now I lost the default desktop manager to kdm the gdm doesnt remain the default desktop manager anymore How to make it the default desktop manager? I tried
```
 sudo /etc/init.d/gdm start
``` but it didnt work

Since you don't want kdm why did you chosse it when you insatled kde, it would have given you the option.
But do this

 Log out of gui
Choose terminal or tty as your login option from kdm log in
 
  sudo apt-get remove kdm
  sudo dpkg-reconfigure gdm

sudo gdm

---

### Post by kanna1620 on 2007-01-25
> **obsidion said:**
> Since you don't want kdm why did you chosse it when you insatled kde, it would have given you the option.
But do this

 Log out of gui
Choose terminal or tty as your login option from kdm log in
 
  sudo apt-get remove kdm
  sudo dpkg-reconfigure gdm

sudo gdm
Thanks. It worked.
And regarding my kde installation:
Actually as KDE provides so many editors and all I wanted to install it but wanted the gdm to remain my default desktop manager.

---

