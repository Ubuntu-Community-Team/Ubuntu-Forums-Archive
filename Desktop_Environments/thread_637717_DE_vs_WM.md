---
title: "DE vs WM"
date: 2007-12-11
forum: Desktop Environments
---

### Post by rob1984 on 2007-12-11
sorry, i still don't get the whole window manager/desktop environment thing.

i understand that the window manager only deals with windows whereas the DE does everything else.  my problem is that this doesnt seem to be the case. if i run my window manager [fluxbox, enlightenment etc..] it seems to deal with everything, not just the windows. also they appear alongside gnome and kde in the sessions menu.

i ask because i like using gnome but id like to use a different window manager, however, if i do run a different WM, it takes over the whole lot.

can anybody dumb it down for me?

---

### Post by ingvildr on 2007-12-11
When you pick a session from the login manager you are picking just fluxbox, enlightenment or gnome to use fluxbox in gnome open a terminal and run fluxbox --replace.

And if you like it you can always save the session.

---

### Post by Thanoulis on 2007-12-11
It is not so complicated as you think it is...:)
Gnome is a Desktop Environment, but it has its own window manager (usually Metacity).
Fluxbox,Enlightenment,IceWM,etc, are just plain window managers that do not work with Gnome or KDE, or XFCE.
Usually they only control your desktop and menus, but they are a lot more customizable, light weighted and funny!
So, you cannot have Gnome Desktop Environment with Fluxbox cumulative, but you can have Fluxbox with some Gnome applications in it!
Hope that helped...:)

---

### Post by mcduck on 2007-12-11
Most window managers come with some kind of dock and other stuff to make them actually usable for doing things. But desktop environments have a lot more, they have their own widget toolkits for drawing program interfaces (GTK and QT), their own window managers (Metacity & Kwin), loads of applications made to work together, configuration tools and other stuff that simple window managers do not have or are not able to handle..

And like said, you can use some other window manager to manage windows in Gnome and KDE (Compiz Fusion, for example), but if you remove Fluxbox from Fluxbox there really is nothing left. ;)

It's actually possible to replace Metacity in Gnome with Fluxbox or Kwin or some other window manager.

---

### Post by sirdilznik on 2007-12-11
I think mcduck summed it up pretty well.  Just to put it is short, easy terms.  A WM just manages the actual windows that display and a few other basic functionalities while a DE is a WM plus a whole lot more.

---

### Post by rob1984 on 2007-12-11
> When you pick a session from the login manager you are picking just fluxbox, enlightenment or gnome to use fluxbox in gnome open a terminal and run fluxbox --replace.

And if you like it you can always save the session.

thanks! thats exactly what i wanted

---

### Post by rob1984 on 2007-12-11
> to use fluxbox in gnome open a terminal and run fluxbox --replace.

help! this doesnt work.

```
BScreen::BScreen: an error occured while querying the X server.
             another window manager already running on display:0.0
             Error: Couldn't find screens to manage.
             Make sure you don't have another window manager running.
```

---

### Post by mali2297 on 2007-12-11
Try
```

pkill metacity && fluxbox &

```

---

### Post by rob1984 on 2007-12-11
that just kills metacity and doesnt start fluxbox. i have to log out to fix it.

is there not a graphical tool to change the window manager?
what's the command to print what DE & WM i'm using?

what do all th &'s mean?

---

### Post by mcduck on 2007-12-11
> **rob1984 said:**
> that just kills metacity and doesnt start fluxbox. i have to log out to fix it.

is there not a graphical tool to change the window manager?
what's the command to print what DE & WM i'm using?

what do all th &'s mean?

I'm pretty sure there isn't a GUI tool for this. It's not something people would usually do.

"&&" in command line means that if the command before it is exxecuted succesfully the command after it should be executed as well. You can use this to chain commands together. For example "sudo apt-get update && sudo apt-get upgrade" will first run "sudo apt-get update" and when that's done it runs "sudo apt-get upgrade".

"&" at the end of a command means that the command should be executed in background, leaving the terminal usable for other tasks.

---

### Post by aysiu on 2007-12-11
Alt-F2 ```
fluxbox --replace
``` should do it.

By the way, a desktop environment usually includes a window manager and a whole bunch of applets and services. A window manager usually won't allow much interactivity with the desktop or desktop icons, have a trash can, or automount external media. All it does is manage windows.

---

### Post by PeterJS on 2007-12-11
The && means only run the command after them if the command before them succeeds. So in this case only try to launch fluxbox if you close metacity successfully. The & after fluxbox means to run fluxbox in the background of the terminal, so you can close the terminal with out closing fluxbox.

---

### Post by rob1984 on 2007-12-12
ive tried -- replace, it doesnt work.

i get the error message like the post above.

---

