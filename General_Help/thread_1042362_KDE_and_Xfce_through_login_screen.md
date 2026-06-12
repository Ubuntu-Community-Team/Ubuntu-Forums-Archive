---
title: "KDE and Xfce through login screen?"
date: 2009-01-17
forum: General Help
---

### Post by gaalaaant on 2009-01-17
Hey guys, I was reading ashpringle's blog about switching to Ubuntu for a week.  He mentioned being able to toggle between KDE and Gnome through the login screen and I was wondering how I could do this except between GNOME, KDE, and Xfce.  Currently I am under GNOME.

---

### Post by Yellow Pasque on 2009-01-17
If you're using the standard gdm login, just change the session (in that menu in the lower left).

---

### Post by abn91c on 2009-01-17
after installing the kde, xfce desktops they will be under "**sessions**" in the log in screen

---

### Post by adult swim on 2009-01-17
youd have to go to a terminal, applications>accessories>terminal and enter in ```
sudo apt-get install xubuntu-desktop kubuntu-desktop
``` it will ask for your password, type taht in and hit enter.  after it gets finished, youll need to log out and when you get to the login screen, go down to options.  select sessions and choose xfce, kde, or gnome.

---

### Post by gaalaaant on 2009-01-17
which display manager should I use? 
I got this message

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring kdm &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; A display manager is a program that provides graphical login              &#9474; 
 &#9474; capabilities for the X Window System.                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Only one display manager can manage a given X server, but multiple        &#9474; 
 &#9474; display manager packages are installed. Please select which display       &#9474; 
 &#9474; manager should run by default.                                            &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Multiple display managers can run simultaneously if they are configured   &#9474; 
 &#9474; to manage different servers; to achieve this, configure the display       &#9474; 
 &#9474; managers accordingly, edit each of their init scripts in /etc/init.d,     &#9474; 
 &#9474; and disable the check for a default display manager.                      &#9474; 
 &#9474;

---

### Post by abn91c on 2009-01-17
> **gaalaaant said:**
> which display manager should I use? 
I got this message

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring kdm &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; A display manager is a program that provides graphical login              &#9474; 
 &#9474; capabilities for the X Window System.                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Only one display manager can manage a given X server, but multiple        &#9474; 
 &#9474; display manager packages are installed. Please select which display       &#9474; 
 &#9474; manager should run by default.                                            &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Multiple display managers can run simultaneously if they are configured   &#9474; 
 &#9474; to manage different servers; to achieve this, configure the display       &#9474; 
 &#9474; managers accordingly, edit each of their init scripts in /etc/init.d,     &#9474; 
 &#9474; and disable the check for a default display manager.                      &#9474; 
 &#9474;
GDM To make Ubuntu the default

---

