---
title: "i3 no windows, no menu"
date: 2021-10-13
forum: Desktop Environments
---

### Post by maurice-volaski on 2021-10-13
I logged in Ubuntu [COLOR=#000000][FONT=Menlo]20.04.1 and chose the i3 window manager. I chose the default configuration. I have a mostly black screen with a 1 icon in the lower left and some machine info printed along the bottom at the right. There are no windows, no menus and no way to get to them or to access a terminal to print the env variables. What am I missing? It's as if the desktop environment isn't being tied to i3.[/FONT][/COLOR]

---

### Post by ajgreeny on 2021-10-13
Do you have any other DE or window manager available to login to at the login screen?

I do not know i3 at all so can not help or tell you of a way out of the GUI it gives you, but try Ctrl+Alt+F2 to get to a TTY command line, and login there, from where you can shutdown with command ```
sudo shutdown -P
``` or reboot with ```
sudo shutdown -r now
```
I think you will need sudo for both those commands as you will still be logged into the i3 session so will be unable to shutdown as user if you can not log out from i3 first.

At your next boot after the shutdown or reboot choose the alternative DE at the login screen and you should be back to normal.

---

### Post by ActionParsnip on 2021-10-13
Pressing CTRL + ALT + T will launch a terminal

---

### Post by maurice-volaski on 2021-10-13
Thanks for your reply, but I can trivially switch to Ubuntu's window manager. I am trying to figure out why i3 is not giving me any windows or menus. It&#8217;s as if it should be tied to some desktop environment, but isn&#8217;t.

---

### Post by maurice-volaski on 2021-10-13
I&#8217;m not trying to launch a terminal just to get a terminal. I&#8217;m trying to figure out why i3 is broken.

---

### Post by grahammechanical on 2021-10-13
It seems that the i3 window manager is coded for the X11 display server. Who knows what will happen if Ubuntu is set to use the Wayland window compositor. It might also be useful to know something about i3 and how to use it.

[https://www.zdnet.com/article/how-to-customise-your-linux-desktop-i3-window-manager/](https://www.zdnet.com/article/how-to-customise-your-linux-desktop-i3-window-manager/)

There is an image on the web page that shows how i3 looks on Manjaro. 

> I think that the single most important concept in i3 is the Modifier key, which I will refer to in the rest of this post as *Mod-*.    This is the key you press and hold together with other keys to  perform basic actions such as opening new windows or moving between  windows.  This is likely to be either the *Alt* key or the *Super* key (aka Window key) on most installations and keyboards - in Manjaro i3 it is *Super* by default.

> Let's take the first leap, and open a window on i3.  One of the simplest is a terminal window, which can be opened by pressing *Mod-Enter*.

This is how to install i3 on Ubuntu. Did you fail to install all the bits?

[https://kifarunix.com/install-and-setup-i3-windows-manager-on-ubuntu-20-04/](https://kifarunix.com/install-and-setup-i3-windows-manager-on-ubuntu-20-04/)

---

### Post by DuckHook on 2021-10-13
> **maurice-volaski said:**
> &#8230;I&#8217;m trying to figure out why i3 is broken.
i3 is not broken. As a Window Manager, it actually sits at a more foundational level in your GUI stack and therefore does not come with the eye candy that makes up a typical _D_esktop _E_nvironment. Since it is designed to forego the bloat and cruft of a DE, it works through keyboard shortcuts and config files as a tiling _W_indow _M_anager _E_nvironment.

Please see the link in my sig: *The Best 'buntu Flavour*

The i3 WME is explained and illustrated in brief as the last entry in the section: *Alternative Window Manager Environments*

The preceding material explains what WMEs are and how/why they differ from DEs.

---

### Post by tea for one on 2021-10-14
> **maurice-volaski said:**
> I logged in Ubuntu [COLOR=#000000][FONT=Menlo]20.04.1 and chose the i3 window manager. I chose the default configuration. I have a mostly black screen with a 1 icon in the lower left and some machine info printed along the bottom at the right. There are no windows, no menus and no way to get to them or to access a terminal to print the env variables. What am I missing? It's as if the desktop environment isn't being tied to i3.[/FONT][/COLOR]

Plenty of information in the user's guide [https://i3wm.org/docs/userguide.html#_using_i3](https://i3wm.org/docs/userguide.html#_using_i3)

---

### Post by maurice-volaski on 2021-10-14
OK, so now I understand. My next question is how can I make this work with RDP/VNC. When I try with RDP, I do see the i3 window, but the $mod key is being ignored for some reason.

---

### Post by QIII on 2021-10-14
Hello!

Please start a new thread for your second question.  We would like to have only one question per thread to avoid confusion.  Your new question is really about remote access/remote behavior.

If you original issue was resolved, please mark the thread "Solved" by using the Thread Tools drop down in the upper right.

---

