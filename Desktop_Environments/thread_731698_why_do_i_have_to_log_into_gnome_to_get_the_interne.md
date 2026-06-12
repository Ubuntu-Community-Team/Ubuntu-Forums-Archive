---
title: "why do i have to log into gnome to get the internet to work in fluxbox?"
date: 2008-03-22
forum: Desktop Environments
---

### Post by jorik42 on 2008-03-22
so, i have this odd problem.  in order to utilize the internet from fluxbox, i first have to log into gnome, connect, then log back into fluxbox.  any idea of why this is and how to fix it?

also, when fluxbox first initializes, the resolution and some functionality are off.  ie, the screen resolution is wrong and some buttons (like the volume scroll wheel) dont work.  yet, if i run the totem media player app ( "totem" from the command line), everything fixes itself - screen resolution, buttons, ect.  also, when this fix happens, parts of my gnome themes appear in fluxbox (like my cursor theme, for instance).  again, does anyone have any ideas as to why this is?


thanks
    jorik

---

### Post by Lord Illidan on 2008-03-22
Are you using networkmanager in Gnome?

---

### Post by jorik42 on 2008-03-22
im not sure; im using whatever the gnome default is.  how would i check?

---

### Post by spupy on 2008-03-22
Gnome runs a daemon program called gnome-setting-daemon. It makes gtk programs use the theme you selected, puts the cursor theme, makes gnome keybindings work, and other stuff. Gnome also has a program which automatically connects you to the internet when you plug in the cable.
Fluxbox doesn't start these things. Since fluxbox is not a Desktop Environment, just a Window Manager, it doesn't have these kind of helper programs.

Here is how you can start these programs when fluxbox starts:

Open the file ".fluxbox/startup" in gedit. Add these lines (**but don't add them to the end!**):
gnome-settings-daemon &
gnome-network-manager &

(i'm not sure if that was the correct name for the network manager)

---

### Post by DaV|d on 2008-03-22
also if you have a pppoe connection, when you run pppoeconfig to set up your internet connection, you have an option to connect at bootup. Just enable that option (and make sure your modem is on while booting)

---

### Post by cevans on 2008-03-22
> **spupy said:**
> Gnome runs a daemon program called gnome-setting-daemon. It makes gtk programs use the theme you selected, puts the cursor theme, makes gnome keybindings work, and other stuff. Gnome also has a program which automatically connects you to the internet when you plug in the cable.
Fluxbox doesn't start these things. Since fluxbox is not a Desktop Environment, just a Window Manager, it doesn't have these kind of helper programs.

Here is how you can start these programs when fluxbox starts:

Open the file ".fluxbox/startup" in gedit. Add these lines (**but don't add them to the end!**):
gnome-settings-daemon &
gnome-network-manager &

(i'm not sure if that was the correct name for the network manager)

Network manager is always running, unless it has been disabled - it's started by the dbus system startup. However, network manager doesn't work very well unless the systray applet is present, which is one of the reasons I really dislike it at present (there is no way to control it from the terminal without raw dbus messages, as far as I can tell - I need to write a program to do this).

To do this with fluxbox, one will need a systray of some sort. stalonetray and trayer are both in universe, and would both work. After starting one of these, start nm-applet, which is the applet that controls NetworkManager. (gnome-network-manager used to be the name of the applet, but no longer works, if I recall correctly)

Of course, this forces one to have a systray sitting on one's desktop, which is horrible for users of window managers like wmii, but shouldn't be that much of a problem for fluxbox users.

The other problems are caused by the lack of gnome-settings-daemon. While one can operate without it, it is usually far easier to just have it running; otherwise, gtkrc files and whatnot need to be created manually.

---

### Post by spupy on 2008-03-22
> **cevans said:**
> To do this with fluxbox, one will need a systray of some sort. stalonetray and trayer are both in universe, and would both work. After starting one of these, start nm-applet, which is the applet that controls NetworkManager. (gnome-network-manager used to be the name of the applet, but no longer works, if I recall correctly)

Of course, this forces one to have a systray sitting on one's desktop, which is horrible for users of window managers like wmii, but shouldn't be that much of a problem for fluxbox users.

Fluxbox does have a system tray, will it do?

---

### Post by cevans on 2008-03-22
> **spupy said:**
> Fluxbox does have a system tray, will it do?

I'm afraid I'm a rather old Linux user, and most of the time I've spent running Linux was before the systray standard even existed. I'm almost certain that Fluxbox's system tray will work, but it certainly didn't have one when I used it!

---

### Post by jorik42 on 2008-03-22
cevans was correct; the systray in fluxbox does work, though installing one of the other spps (stalonetray, trayer) work as well.  just add the "nm-applet &" to your fluxbox startup file, and youre in business!  

thanks all!

jorik

---

