---
title: "I have a problem with the windows"
date: 2010-06-30
forum: Desktop Environments
---

### Post by booterror on 2010-06-30
I tried enlightenment and I didn't like how it worked, so I uninstalled it. I don't know what happened. It wrecked all my windows and I can't connect to the internet now. the bar at the top of every window is gone, and my network icon is gone from the toolbar. How do i put it back the way it was?

---

### Post by wilee-nilee on 2010-06-30
> **booterror said:**
> I tried enlightenment and I didn't like how it worked, so I uninstalled it. I don't know what happened. It wrecked all my windows and I can't connect to the internet now. the bar at the top of every window is gone, and my network icon is gone from the toolbar. How do i put it back the way it was?

At the login window you can choose the desktop, if you have only had enlightenment then install another desk top from the command line in recovery.

---

### Post by booterror on 2010-06-30
I had e16 + Gnome. it changed the little bars at the top of the windows, but still looked like Gnome. I took e16 off, and tried to use regular Gnome. Gnome is the only one on it now. How do I reinstall it?

---

### Post by booterror on 2010-06-30
Ok I figured out how to do ```
metacity --replace
``` in the terminal. how do I save it?

---

### Post by wilee-nilee on 2010-06-30
> **booterror said:**
> Ok I figured out how to do ```
metacity --replace
``` in the terminal. how do I save it?

I think gnome is basically the Ubuntu desktop here is a link that will probably help.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Choose your distro and just use the sliding list to reinstall. I don't know whats on the computer so this is probably your best approach.

Actually the link I gave you is for removing other desktops, just run in the terminal
```
sudo apt-get install ubuntu-desktop
```

---

### Post by booterror on 2010-06-30
I have gnome on it. I just don't seem to have a window manager.

When I try to go to the window settings in preferences it says 'Cannot start the preferences application for your window manager. Window manager "unknown" has not registered a configuration tool.'

---

### Post by CJ_Hudson on 2010-06-30
I don't want to sound mendacious but I think your computer has been taken over by the little green men!

---

### Post by booterror on 2010-06-30
got the solution from reddit. 

"open gconf-editor and go to *desktop->gnome->session->required_components*  and change the windowmanager key value to *metacity"*

---

