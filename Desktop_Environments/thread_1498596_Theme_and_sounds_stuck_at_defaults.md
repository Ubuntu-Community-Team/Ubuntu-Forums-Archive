---
title: "Theme and sounds stuck at defaults"
date: 2010-06-01
forum: Desktop Environments
---

### Post by ubuntwinkel on 2010-06-01
Sorry to start another thread, but I cannot find anything remotely close to a solution anywhere.  Searching for days.

The problem started after my system froze and I had to push reset to restart.  (Was editing a big mp3 with audacity.)  Since then, the theme is stuck at Clearlooks--the default, and system sounds (mouse clicks, windows closing, etc) are stuck on (I had them set to 'off'--the default is 'on'). 

Changing appearance settings only changes the appearance of the *appearance preferences* popup.  System stays stuck on Clearlooks.  Shutting off sounds in *sound preferences* has no effect either.

It is not only themes which are broken, but sounds, too.  And I suspect some other less obvious settings which I haven't discovered yet are stuck as well.  Also, I created a brand-new user to test if this was something corrupted in just my user settings only, but the problem persists, even for a new user.  

I've rebooted a hundred times.  I have purged and reinstalled everything I could think of, including compiz, all themes, and metacity.  I've searched through gconf-editor, combed through hidden and system folders, and searched countless web pages.  The problem is utterly unaffected by everything I have tried; nothing makes it worse, nothing improves it even slightly.  

I started with Dapper long ago, so I'm not a newbie, but I am far from expert.  And this has me completely stumped.  This seems to have something to do with Gnome and the way it handles system-wide settings, maybe?  

I am open to anything and will hugely appreciate all your ideas.  

**UPDATE:**
Very oddly, I am able to change window borders via *customize theme*, from within the *appearance preferences* popup, but nothing else.

---

### Post by ubuntwinkel on 2010-06-01
Additionally, I am planning to upgrade to Lucid.  But I wanted to resolve this first, since I fear it will persist across the upgrade.  

Any ideas on doing an upgrade as a solution?  Or any other solution?  

Thanks!

---

### Post by ubuntwinkel on 2010-06-02
Upgraded to Lucid.  Condition persists.  Cannot change window theme, or change sound settings. :(  

Anybody?

---

### Post by ubuntwinkel on 2010-06-03
Hoping...

---

### Post by ubuntwinkel on 2010-06-04
For completeness, it is now fixed, and I think this is what fixed it: (from synaptic history)
> Completely removed the following packages:
gnome-accessibility-themes
gnome-themes
gnome-themes-extras
gnome-themes-more
gnome-themes-selected
gnome-themes-ubuntu
gtk2-engines
gtk2-engines-murrine
light-themes
murrine-themes
ubuntu-artwork
ubuntu-desktop
(aka "apt-get purge")

...and then installed (or reinstalled): 
> Installed the following packages:
avant-window-navigator (0.4.0-0ubuntu1)
avant-window-navigator-data (0.4.0-0ubuntu1)
awn-applets-c-core (0.4.0-0ubuntu1)
awn-applets-python-core (0.4.0-0ubuntu1)
awn-settings (0.4.0-0ubuntu1)
bzr (2.1.1-1)
bzrtools (2.1.0-1)
fortune-mod (1:1.99.1-3.1ubuntu4)
fortunes-min (1:1.99.1-3.1ubuntu4)
gnome-themes (2.30.0-0ubuntu1)
gnome-themes-extras (2.22.0-3)
gnome-themes-more (0.9.0.deb0.7)
gnome-themes-selected (2.30.0-0ubuntu1)
gtk-clearlooks-gperfection2-theme (1.1-0ubuntu2)
gtk2-engines (1:2.20.0-0ubuntu1)
gtk2-engines-nodoka (0.7.2-0ubuntu1)
libawn1 (0.4.0-0ubuntu1)
libdesktop-agnostic-cfg-gconf (0.3.90-0ubuntu1)
libdesktop-agnostic-fdo-glib (0.3.90-0ubuntu1)
libdesktop-agnostic-vfs-gio (0.3.90-0ubuntu1)
libdesktop-agnostic0 (0.3.90-0ubuntu1)
python-awn (0.4.0-0ubuntu1)
python-awn-extras (0.4.0-0ubuntu1)
python-desktop-agnostic (0.3.90-0ubuntu1)
python-gweather (2.30.0-0ubuntu1)
python-paramiko (1.7.6-2)


The awn packages were included just because I had issues with it once ages ago, and somewhere in the 500 web pages I've read on this topic, somebody mentioned awn was a culprit.  I actually thought if I reinstalled awn, and then purged it, that might work.  I never got as far as purging awn.  With the above reinstalls, the window-controls, decorations, (and theme in general) all came back.  

Control of sounds seems to be back too, though I won't be sure until after a reboot.

I would guess that the purge-reinstall of gtk2-engines is what did it, but I am almost certain I did that before, and it didn't resolve the issue.  So, who knows?  If you see something here that makes sense, make a note because I would love to know what was wrong, and how it finally got itself fixed.

---

