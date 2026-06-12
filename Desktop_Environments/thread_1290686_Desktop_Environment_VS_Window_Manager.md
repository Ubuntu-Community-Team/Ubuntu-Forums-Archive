---
title: "Desktop Environment VS Window Manager"
date: 2009-10-13
forum: Desktop Environments
---

### Post by magicmax0 on 2009-10-13
First of all, whats the difference, if any. If they are different, which default "Window Managers" do KDE, GNOME, and XFCE use? 

Lastly, which dekstop environment and/or window manager (or combination thereof) would you reccomend for someone whos priority is speed (GNOME loads/runs slow for me), multiple workspace support, and (most important) stability (specifically when running 3D games or movies in window or full screen mode, GNOME seems to be unstable for me no matter what i try.)

Besides GNOME being slow and unstable, i love everything about it (look, animations, configuration options). But its just not enough to overcome the fact it crashes alot and loads slow. Im not sure if it means anything, but i have a quad core AMD CPU, AMD790X series mobo, 4GB RAM (i run 64bit ubuntu) and an ATI 4870 GPU.

---

### Post by jeremyswalker on 2009-10-13
Well, after a quick Google search, I uncovered a link that may offer you some enlightenment on the subject: [http://www.ghacks.net/2008/12/09/get-to-know-linux-desktop-environment-vs-window-manager/]("http://www.ghacks.net/2008/12/09/get-to-know-linux-desktop-environment-vs-window-manager/"). Basically, a window manager, in its basic form, handles displaying window borders and such. A desktop environment includes extra applications; such as a session manager, panel, file browser, etc.

KDE uses kwin
Gnome uses metacity
XFCE uses xfwm

XFCE would get you the speediest desktop on older hardware.

---

### Post by XubuRoxMySox on 2009-10-13
I disagree.... Xfce has been the traditionally "lightweight" desktop environment, but a new arrival is changing that. 

Just for fun, install LXDE (available in Synaptic) and give it a spin. In my opinion it's a little more intuitive than Xfce, and *definitely* much faster and much more lightweight. Very few dependencies, very light and fast on older hardware.

-Robin

---

### Post by anonymous_user on 2009-10-13
Don't forget LXDE which uses Openbox.

---

### Post by jeremyswalker on 2009-10-13
Ok. Yeah, I didn't even think about LXDE. It's been awhile since I used it. Yeah, LXDE would be an excellent lightweight desktop to use.

---

### Post by MelDJ on 2009-10-14
see this: [http://xwinman.org/](http://xwinman.org/)

---

### Post by XubuRoxMySox on 2009-10-14
> **MelDJ said:**
> think the world of linux only has kde, gnome, xfce and lxde? 
think again. see this: [http://xwinman.org/](http://xwinman.org/)

That site lists several *window managers* but only _four_ *desktop environments* (and it doesn't list LXDE among them, nor Enlightenment). **There is a difference!** 

And yes, there are lots of different *window managers* to choose from. Some seem to have fallen by the wayside and some have risen to prominence. Openbox, for example, is awesome-looking and powerful without the need for desktop environment at all (Crunchbang Linux is an amazing implementation of it)! LXDE relies heavily on Openbox, which is one of the reasons why it's so awesome in spite of it's gravity-defying weightlessness.

-Robin

---

### Post by MelDJ on 2009-10-14
> **dixiedancer said:**
> That site lists several *window managers* but only _four_ *desktop environments* (and it doesn't list LXDE among them, nor Enlightenment). **There is a difference!** 

And yes, there are lots of different *window managers* to choose from. Some seem to have fallen by the wayside and some have risen to prominence. Openbox, for example, is awesome-looking and powerful without the need for desktop environment at all (Crunchbang Linux is an amazing implementation of it)! LXDE relies heavily on Openbox, which is one of the reasons why it's so awesome in spite of it's gravity-defying weightlessness.

-Robin

ah yes.. i forgot that those were actually window managers and not DE's. ah...the shame...

---

### Post by slakkie on 2009-10-14
> **dixiedancer said:**
> That site lists several *window managers* but only _four_ *desktop environments* (and it doesn't list LXDE among them, nor Enlightenment). **There is a difference!** 


It is listed.. 
> 
Source: [http://xwinman.org/otherdesktops.php](http://xwinman.org/otherdesktops.php)

 Here is a list of other desktop environments I've heard about. If you know of any others, or think I should feature any of them in more detail, please let me know.

See also the Other Window Managers page.

    * LXDE: The Lightweight X11 Desktop Environment is especially designed for computers with low hardware specifications like netbooks and mobile devices.


For me a DE is: A WM bundeled with all kinds of applications. 

A WM is just something that manages windows and doesn't provide  applications, that is something you must cherry pick.

A DE is more complete in that sense, since you can install it and do basic work on it, where as a WM does not.

---

### Post by magicmax0 on 2009-11-09
Thanks for the enlightenment guys. I've since tried XFCE and found it much faster than GNOME. I also tried KDE and found it even worse then GNOME. I did try LXDE also, its definitely more lightweight than XFCE (seems XFCE is getting alot heavier lately). However, i prefer the look and feel of XFCE. I liked LXDE's File manager (PCman) and window manager (openbox) very much, but found it lacking most of the other basic programs i needed (i know i could install them manually but there were TUNS). I will definitely keep LXDE as an option in the future, i cant wait until Lubuntu (LXDE spin on ubuntu) makes its first release, which is planned for version 10.04 LTS. Till then im sticking to XFCE, Xubuntu 9.10 amd64.

PS: For LXDE, i tried the ubuntu minimal install (9.10amd64)  + lxde-desktop package. I also tried the Debian 503 LXDE spin also, which i found identical to ubuntu's spin.

---

