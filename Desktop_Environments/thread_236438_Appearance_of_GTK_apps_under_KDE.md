---
title: "Appearance of GTK apps under KDE"
date: 2006-08-14
forum: Desktop Environments
---

### Post by ahaslam on 2006-08-14
Hello,

I have Gnome, Xfce & Kde installed. I like all of them for different reasons and use them all frequently. One thing that I can't understand is how bad Gtk apps look under Kde, as Xfce & Gnome display Qt apps perfectly.

A member of this forum suggested I try "gtk2-engines-gtk-qt". At first glance it worked perfectly, allowing me to select a theme for Gtk apps. A problem was apparent when I logged in to Xfce and noticed that my custom theme was replaced by the Kde style. The same was also apparent under Gnome, along with a few error messages at start up.

I have now uninstalled this utility, but still wish to address the appearence of Gtk themes under Kde - without disrupting Xfce of Gnome. I'm sure someone's fixed it, what do I need to do?

Thank you,

Tony.

---

### Post by gunksta on 2006-08-14
KDE wants to control the GTK theme, which is the problem you are facing. In the KDE control center, set the GTK theme, and all GTK apps will inherit this theme when started under KDE.

--andy

---

### Post by jasutton on 2006-08-14
I don't know about everyone else, but I use a little app called gtk-chtheme.  Whenever I install Ubuntu/Debian, it's almost the first thing I do.  I compiled it under Breezy and rolled a quick DEB (works fine in Dapper too).  You can download it at:

[http://jaredsutton.com/downloads/gtk-chtheme-0.3.1_i386.deb](http://jaredsutton.com/downloads/gtk-chtheme-0.3.1_i386.deb)

Hope that helps :)

---

### Post by ahaslam on 2006-08-15
> **gunksta said:**
> KDE wants to control the GTK theme, which is the problem you are facing. In the KDE control center, set the GTK theme, and all GTK apps will inherit this theme when started under KDE.

--andy
That's great under Kde but it also sets the same theme for Xfce & Gnome :( 

Tony.

---

### Post by ahaslam on 2006-08-15
> **jasutton said:**
> I don't know about everyone else, but I use a little app called gtk-chtheme.  Whenever I install Ubuntu/Debian, it's almost the first thing I do.  I compiled it under Breezy and rolled a quick DEB (works fine in Dapper too).  You can download it at:

[http://jaredsutton.com/downloads/gtk-chtheme-0.3.1_i386.deb](http://jaredsutton.com/downloads/gtk-chtheme-0.3.1_i386.deb)

Hope that helps :)

Thanks for the Deb, I'm sure people using only KDE would appreciate it.
Unfortunately it also changes the theme under all DE's. What's worse is that after uninstalling, I've still got the same theme & I can't change it ](*,) 

Tony.

---

### Post by ahaslam on 2006-08-15
I fixed the problem by deleting all files starting with ".gtk" within my home folder.

I still want to find a way to change the appearance of gtk apps under kde, **without affecting gnome or xfce** - any ideas?


Tony.

---

### Post by jasutton on 2006-08-16
Well, I'm not sure if such a thing really exists.  I mean, GTK really is not dependent on the particular DE in use to get it's configuration.  So, changing the theme for GTK in one is obviously going to have the same effect on the other DEs.

Now, an interesting work-around would be to find some command-line app that would allow you to modify the GTK theme.  Then, you could script something that would detect what DE you're using and change the GTK theme for you.

Personally, I just find a theme that looks good in all DEs, such as Clearlooks. ;)

---

### Post by ahaslam on 2006-08-17
> **jasutton said:**
> Well, I'm not sure if such a thing really exists.  I mean, GTK really is not dependent on the particular DE in use to get it's configuration.  So, changing the theme for GTK in one is obviously going to have the same effect on the other DEs.
I can set different themes for Xfce & Gnome, with no such conflictions :-k 

> **jasutton said:**
> Now, an interesting work-around would be to find some command-line app that would allow you to modify the GTK theme.  Then, you could script something that would detect what DE you're using and change the GTK theme for you.
That does sound interesting, any ideas on how to go about it?

Cheers,

Tony.

---

### Post by jasutton on 2006-08-17
Well, I found a nice little app for changing the GTK+ 2.0 theme on the command line.  It's called gtk-theme-switch2 ("apt-get install gtk-theme-switch").  With that, you can simply run "gtk-theme-switch2 [path to theme dir]".  For example, if I wanted to change to Clearlooks from something else, I would do "gtk-theme-switch2 /usr/share/themes/Clearlooks/".

On the scripting, I would write a bash script that would check to see if a particular program was running to detect each DE.  For example, kwin (the KDE Window Manager) would most likely be running if you had an open KDE session.  The exception to that would be if you specifically used a different window manager (for example, if you used XGL+Compiz for pretty GUI effects).  Anyway, baring that exception, you could write your script like this (I'll only do the KDE detection, as that's the only desktop I normally use):

```
#!/bin/bash

# check to see if kdm is running
pidof kdm

#if so, change GTK theme to Qt
if [ $? -eq 0 ]; then
  gtk-theme-switch2 /usr/share/themes/Qt
  exit 0
fi
```

You could do the other desktops likewise, and just mark that script executable (chmod +x [script-name]), and make sure to make it starts automatically when you log in (for example, you could include a symlink for it in "~/.kde/Autostart" to start it when KDE does; it would be different for other DEs).

Anyway, I hope that helps :)

---

### Post by ahaslam on 2006-08-18
> **jasutton said:**
> Well, I found a nice little app for changing the GTK+ 2.0 theme on the command line.  It's called gtk-theme-switch2 ("apt-get install gtk-theme-switch").  With that, you can simply run "gtk-theme-switch2 [path to theme dir]".  For example, if I wanted to change to Clearlooks from something else, I would do "gtk-theme-switch2 /usr/share/themes/Clearlooks/".

On the scripting, I would write a bash script that would check to see if a particular program was running to detect each DE.  For example, kwin (the KDE Window Manager) would most likely be running if you had an open KDE session.  The exception to that would be if you specifically used a different window manager (for example, if you used XGL+Compiz for pretty GUI effects).

Thank you :) That was just what I needed.
I adapted the script slightly, writing one for Kde & another for Gnome & Xfce. Here's a few screens that show how & the effect ;)

[ATTACH]14501[/ATTACH][ATTACH]14502[/ATTACH][ATTACH]14503[/ATTACH]

Thanks again, even if you don't choose to create the scripts, the command line is really quick & easy ;)

Greatly appreciated,

Tony :D

---

### Post by jasutton on 2006-08-19
Just a quick note about my original script...Looks like I made a slight typo (twice).  I apparently had it check for kdm to be running instead of kwin.  So, that wouldn't be very useful would it now? :D

---

