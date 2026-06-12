---
title: "How do I set the default window manager?"
date: 2011-03-25
forum: Desktop Environments
---

### Post by fivebells on 2011-03-25
I have a pretty vanilla install of Ubuntu Lucid.  I would like to change my default WM to sawfish.  I have it installed, and it works routinely, I would just like to have it start automatically on log-in, rather  than Lucid.  

A few sources have suggested that the way to do this is during log-in.  They refer to a "session" I could choose, which would allow me to set the WM.  I remember doing this in the past, but can't find such an option on the login page, now.

I have also experimented with changing .gconf/desktop/gnome/applications/window_manager/ using both gconf-editor and emacs.  However, when I change "/usr/bin/compiz" to "/usr/bin/sawfish", log out, and log back in, I find that compiz starts anyway, and the setting in that file has been restored to compiz.  Clearly, the gconf mechanism is getting the information from some other source.

---

### Post by frenchn00b on 2011-03-25
> **fivebells said:**
> I have a pretty vanilla install of Ubuntu Lucid.  I would like to change my default WM to sawfish.  I have it installed, and it works routinely, I would just like to have it start automatically on log-in, rather  than Lucid.  

A few sources have suggested that the way to do this is during log-in.  They refer to a "session" I could choose, which would allow me to set the WM.  I remember doing this in the past, but can't find such an option on the login page, now.

I have also experimented with changing .gconf/desktop/gnome/applications/window_manager/ using both gconf-editor and emacs.  However, when I change "/usr/bin/compiz" to "/usr/bin/sawfish", log out, and log back in, I find that compiz starts anyway, and the setting in that file has been restored to compiz.  Clearly, the gconf mechanism is getting the information from some other source.


cd ; 
less .dmrc

or .xinitrc if you start with startx 

or into gdm setup

---

### Post by fivebells on 2011-03-25
Well, I'd like to keep the gnome panel etc, just run sawfish instead.  I think what you're suggesting would take me out of the gnome landscape altogether, although sawfish runs just fine with gnome if I start it from the CL.  (I have figured out how to start sawfish from the gdm login dialog, but that doesn't start gnome...)

---

### Post by Krytarik on 2011-03-25
You shouldn't simply edit the Gconf config files manually, because they may get overwritten by their cached versions.

Instead use "gconf-editor", you can enable it in the menu editor.
- otherwise press Alt+F2
- enter "gconf-editor"

Set "/usr/bin/sawfish" to all of those keys:
- "/desktop/gnome/applications/window_manager/current"
- "/desktop/gnome/applications/window_manager/default"
- "/desktop/gnome/session/required_components/windowmanager"

Greetings.

---

### Post by filmshane on 2012-06-15
Hello How do I set the WM to start every time the system starts on the command line?

---

### Post by Frogs Hair on 2012-06-15
> **filmshane said:**
> Hello How do I set the WM to start every time the system starts on the command line?

Hello and Welcome 

It would help to start your own thread and describe what window manager and/or desktop environment you are referring to.

---

