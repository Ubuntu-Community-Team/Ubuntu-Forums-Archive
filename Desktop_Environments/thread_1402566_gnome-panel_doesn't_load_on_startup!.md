---
title: "gnome-panel doesn't load on startup!"
date: 2010-02-09
forum: Desktop Environments
---

### Post by tominglis on 2010-02-09
I installed Ubuntu 9.10 on my new ThinkPad T510 yesterday. Everything has gone great, and I have all my apps, settings, and files on there.

Unfortunately when I restarted recently, gnome-panel stopped loading at login. I am able to load it by opening a terminal (I have nautilus-open-terminal) and typing "gnome-panel".

I had done quite a lot of stuff just before this issue arose, but I had just uninstalled gnome-games, gnome-pilot, ubuntuone-client, and rhythmbox, and moved lots of panel icons around using "Main Menu" in "Preferences".

I tried reinstalling the "gnome-panel" package in Synaptic, but I am not sure what else to try doing? Can anyone help? If so, that would be tremendously appreciated!

---

### Post by mcduck on 2010-02-09
Do you get any errors when you start Gnome-panel from a terminal?

Open gconf-editor (just run it from a terminal) and check that desktop/gnome/session/required_components_list -key has "panel" in the list, and /desktop/gnome/session/required_components/panel is set to "gnome-panel".

If everythng else fails, you can just add "gnome-panel" to your startup applications. Not very smooth way to handle it but at least it will work if you can't figure out why Gnome isn't loading the panel automatically for you.

---

### Post by dE_logics on 2010-02-09
> **tominglis said:**
> I installed Ubuntu 9.10 on my new ThinkPad T510 yesterday. Everything has gone great, and I have all my apps, settings, and files on there.

Unfortunately when I restarted recently, gnome-panel stopped loading at login. I am able to load it by opening a terminal (I have nautilus-open-terminal) and typing "gnome-panel".

I had done quite a lot of stuff just before this issue arose, but I had just uninstalled gnome-games, gnome-pilot, ubuntuone-client, and rhythmbox, and moved lots of panel icons around using "Main Menu" in "Preferences".

I tried reinstalling the "gnome-panel" package in Synaptic, but I am not sure what else to try doing? Can anyone help? If so, that would be tremendously appreciated!

Oh no....

Ubuntu has horrible dependency resolution. Removing one removes the whole desktop environment!! (aaa not exactly, but point is it removes lots of things that you might not like to remove).

---

### Post by tominglis on 2010-02-09
Here's what I get in the Terminal:

tominglis@Diomedes:~/Desktop$ gnome-panel
** (gnome-panel:2262): DEBUG: Adding applet 0.
** (gnome-panel:2262): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:2262): DEBUG: Adding applet 1.
** (gnome-panel:2262): DEBUG: Adding applet 2.
** (gnome-panel:2262): DEBUG: Adding applet 3.
** (gnome-panel:2262): DEBUG: Adding applet 4.
** (gnome-panel:2262): DEBUG: Adding applet 5.
** (gnome-panel:2262): DEBUG: Adding applet 6.
** (gnome-panel:2262): DEBUG: Adding applet 7.
** (gnome-panel:2262): DEBUG: Adding applet 8.
** (gnome-panel:2262): DEBUG: Adding applet 9.
** (gnome-panel:2262): DEBUG: Adding applet 10.

Everything seems fine in gconf-editor.

Which of the packages I removed would cause a dependency problem? I tried doing apt-get install ubuntu-desktop, and it didn't want to put anything back?

---

### Post by mcduck on 2010-02-09
> **dE_logics said:**
> Oh no....

Ubuntu has horrible dependency resolution. Removing one removes the whole desktop environment!! (aaa not exactly, but point is it removes lots of things that you might not like to remove).

No, dependencies are handled in the only way they can be handled. A dependency is a dependency, and always for a reason. If a package didn't actually depend on another package to work correctly it wouldn't be a dependency. ;)

*Ignoring* dependencies would be bad dependency handling.

---

### Post by mcduck on 2010-02-09
> **tominglis said:**
> Here's what I get in the Terminal:

tominglis@Diomedes:~/Desktop$ gnome-panel
** (gnome-panel:2262): DEBUG: Adding applet 0.
** (gnome-panel:2262): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:2262): DEBUG: Adding applet 1.
** (gnome-panel:2262): DEBUG: Adding applet 2.
** (gnome-panel:2262): DEBUG: Adding applet 3.
** (gnome-panel:2262): DEBUG: Adding applet 4.
** (gnome-panel:2262): DEBUG: Adding applet 5.
** (gnome-panel:2262): DEBUG: Adding applet 6.
** (gnome-panel:2262): DEBUG: Adding applet 7.
** (gnome-panel:2262): DEBUG: Adding applet 8.
** (gnome-panel:2262): DEBUG: Adding applet 9.
** (gnome-panel:2262): DEBUG: Adding applet 10.

Everything seems fine in gconf-editor.

Which of the packages I removed would cause a dependency problem? I tried doing apt-get install ubuntu-desktop, and it didn't want to put anything back?
That doesn't sound like a dependency problem, if it was your panel would have been removed, (or it would fail to start if the dependencies were handled incorrectly). Since it loads correctly when started manually there must be some other problem.

Is there a ".xsession-errors" -file in your home directory? Anything interesting in there?

---

### Post by tominglis on 2010-02-09
Here's the output from the latest version of that file:

[http://paste.ubuntu.com/372824/](http://paste.ubuntu.com/372824/)

---

### Post by tominglis on 2010-02-11
I tried adding gnome-panel to my list of Startup Applications, but it didn't startup on reboot, and when I went to take a look at Startup Applications, my entry was no longer there?

---

