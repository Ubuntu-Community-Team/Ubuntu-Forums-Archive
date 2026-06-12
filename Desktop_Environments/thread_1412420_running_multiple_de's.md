---
title: "running multiple de's"
date: 2010-02-21
forum: Desktop Environments
---

### Post by Post Monkeh on 2010-02-21
i've been experimenting the past few days, trying alternatives to the gnome desktop i've been using for the past year.
i managed to get xfce installed alright, but i noticed that when it loads, it loads the same services as when i log into gnome (ie all my custom scripts etc)

i also installed openbox, but it wouldn't let me log in. i suspected this was because of the same issue - loading services that maybe weren't compatible.  so i made a new user and logged straight into openbox and got it running ok.


i know there are different sessions when i'm logging in. isn't each session completely seperate? ie shouldn't i be able to load all the right services for a gnome login, and load a completely different set of services for openbox or xfce?

---

### Post by urukrama on 2010-02-21
How do you login? Do you use GDM or another login manager or startx/xinitrc? How do you launch your custom scripts?

---

### Post by Post Monkeh on 2010-02-21
> **urukrama said:**
> How do you login? Do you use GDM or another login manager or startx/xinitrc? How do you launch your custom scripts?

i use gdm. (i think - it is a default install of ubuntu, just the default login manager)

the custom scripts are launched by adding them to the startup applications in the system>preferences menu.

---

### Post by urukrama on 2010-02-21
By default Openbox loads some Gnome components. Openbox-session looks for an autostart file in ~/.config/openbox/autostart.sh; if that file does not exist, it loads /etc/xdg/autostart.sh. The latter will load gnome-settings-daemon, but as I don't use Gnome I don't exactly know what settings that covers. Try creating a custom autostart.sh file in ~/.config/openbox/ and see what happens.

The XFCE session settings can be found in the xfce4-settings-manager (under Sessions and Startup). You can check there what applications are loaded by default when XFCE is started. 

What do you mean by "[openbox] wouldn't let me log in"? What happens when you do log in. Note that unless gnome-settings-daemon or something similar is loaded, Openbox does not come with any panels, wallpapers, or icons on the desktop, so it might appear nothing is loaded, but if you right click on the desktop you will see the Openbox menu.

---

### Post by Post Monkeh on 2010-02-21
> **urukrama said:**
> By default Openbox loads some Gnome components. Openbox-session looks for an autostart file in ~/.config/openbox/autostart.sh; if that file does not exist, it loads /etc/xdg/autostart.sh. The latter will load gnome-settings-daemon, but as I don't use Gnome I don't exactly know what settings that covers. Try creating a custom autostart.sh file in ~/.config/openbox/ and see what happens.

The XFCE session settings can be found in the xfce4-settings-manager (under Sessions and Startup). You can check there what applications are loaded by default when XFCE is started. 

What do you mean by "[openbox] wouldn't let me log in"? What happens when you do log in. Note that unless gnome-settings-daemon or something similar is loaded, Openbox does not come with any panels, wallpapers, or icons on the desktop, so it might appear nothing is loaded, but if you right click on the desktop you will see the Openbox menu.

it begins to load, but then it just goes back to the login screen.

when i created a brand new user and logged into openbox, it loaded fine (as you say, blank desktop, but i expected that) 
i can only assume it is something in my user profile that is stopping openbox loading.  
btw, i forgot to mention that when i was playing last night i did copy the /etc/xdg/autostart.sh into my ~/.config/openbox dir.

would downloading a different login manager make any difference? i don't really want to mess about too much. the whole reason i'm trying to have multiple de's is to try them out while still having gnome there to fall back on when i need to do something, i'm loath to start fiddling around too much and end up breaking my gnome desktop

---

### Post by Post Monkeh on 2010-02-21
just as a quick example, when i login to xfce, it loads my awn dock, and also the same conky script that i have running on my gnome desktop.

is this normal? is there a way to change it per login session? ie, i might want a different conky script to run when i log in to xfce than when i log in to gnome.

i think the only "custom" items i have in my startup applications for gnome are conky, remuco-vlc, and awn.

i also notice now that i have a few xfce entries in there (power manager, volstatus icon, volume daemon) which surely i don't need on my gnome login.

is this something that just happens with a multiple de setup, or is there a way to totally separate the various login sessions so that each one will only load the programs and services applicable to that desktop environment?

i tried logging into xfce and editing the startup and session options to remove awn and my conky startup script, but on logging back into gnome the change had also effected it, which i don't want. is there no way bar having different users, of having totally seperate setups for each differnt login session?
i want my home folder etc to remain the same, and even the desktop folder is no big deal, but i would like to be able to, say, start one conky script when logging into xfce, and a different one entirely when logging into gnome, then a different one again if i can ever get openbox working under my own login.

---

### Post by SecretCode on 2010-02-21
You might want to look into the .desktop files ... there's an 'OnlyShowIn=' line which you can set to only show in GNOME.

Not sure which directories you need to look in. 

This kind of thing is semi-standardised by [http://freedesktop.org](http://freedesktop.org)

---

### Post by Post Monkeh on 2010-02-21
> **SecretCode said:**
> You might want to look into the .desktop files ... there's an 'OnlyShowIn=' line which you can set to only show in GNOME.

Not sure which directories you need to look in. 

This kind of thing is semi-standardised by [http://freedesktop.org](http://freedesktop.org)

never thought of that, but isn't that just for things like shortcuts and menu entries?

tbh i'm not fussed if my menus are full of entries for all the programs, it's more about what services and applications are actually being loaded at startup, as well as the fact that something in my gnome setup is stopping an openbox session from running.

like i said, i can make a new user and start an openbox session, and fwiw i can also do an openbox --replace and it works fine on my gnome desktop.

i'm watching the football atm so i can't try anything, but one thing i haven't tried is doing an openbox --replace on my gnome desktop and then logging out and trying to log in to an openbox session.

---

### Post by SecretCode on 2010-02-21
I'm pretty sure startup applications are also defined as desktop entries. Services are probably another matter.

---

### Post by Post Monkeh on 2010-02-21
> **SecretCode said:**
> I'm pretty sure startup applications are also defined as desktop entries. Services are probably another matter.

actually now that i think about it, the custom autostart entries are desktop files so you're probably right. good man.

my bandwidth is being eaten by the football atm so i can't do much, but at least that sorts one of my problems.

---

### Post by Post Monkeh on 2010-02-21
> **SecretCode said:**
> You might want to look into the .desktop files ... there's an 'OnlyShowIn=' line which you can set to only show in GNOME.

Not sure which directories you need to look in. 

This kind of thing is semi-standardised by [http://freedesktop.org](http://freedesktop.org)

well that works great for choosing which applications load in gnome/xfce. good man.

---

### Post by Post Monkeh on 2010-02-21
right so i tried ctrl&alt&f1 ing and doing an "openbox-session"
that gave me errors about not being able to initialise GTK+. but i half expected that because i wasn't sure if i could run 2 sessions of x.
so instead of that, i logged out, then logged in to an xterminal session, expecting that when i did a  n "openbox-session" that i would get some kid of error that i could at least work on.
but it just loaded correctly and gave me the default grey screen, i could right click and get my menu, everything seemed to be ok.
so why can't i just select the openbox session when i'm logging in via gdm?

---

### Post by Post Monkeh on 2010-02-21
ah, i just found the xsession-errors file

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(openbox:4372): Openbox-WARNING **: Openbox is configured for 4 desktops, but the current session has 1.  Overriding the Openbox configuration.
Openbox-Message: Unable to find a valid menu file "debian-menu.xml"

(gnome-settings-daemon:4426): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
gnome-settings-daemon: Fatal IO error 2 (No such file or directory) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1488 requests (1488 known processed) with 0 events remaining.

```

---

### Post by urukrama on 2010-02-22
This thread is continued here: [http://ubuntuforums.org/showthread.php?p=8862011](http://ubuntuforums.org/showthread.php?p=8862011)

---

