---
title: "Disabling Panel Configuration"
date: 2008-08-26
forum: Desktop Environments
---

### Post by lsutiger on 2008-08-26
I am running Gnome as my desktop, but Ubuntu remove some of the lockdown parameters.
According to [this from Sun]("http://docs.sun.com/app/docs/doc/817-5310/6mkpbn3up?a=view"), there should be a /desktop/gnome/lockdown/lockdown_panel_config key, but it is not there.

Is there anyway to re-enable this key? I tried just setting it but that doesn't work.

Thanx in advance!

---

### Post by mcduck on 2008-08-27
I think the key is in apps/gnome-panel/global/locked-down. (not sure about the whole path, but definitely apps/gnome-panel/..

---

### Post by lsutiger on 2008-08-27
Thanx, but it is not there. In the list it goes from gnome-keyring-manager to gnome-power-manager under /apps
thanx for the reply!

---

### Post by mcduck on 2008-08-27
Sorry about that. I just got back home from work and checked the key, it's apps/panel/global/locked_down. (panel, not gnome-panel).

---

### Post by lsutiger on 2008-08-27
Much appreciated!!! 

Now if I could only figure out a way to disable the right click menu on desktop or even edit it!

---

### Post by lsutiger on 2008-08-27
Or even better, what is the program responsible for adding a launcher to desktop from right-click--> Create Launcher?

---

### Post by mcduck on 2008-08-27
I suppose Nautilus handles it, like everything else on the desktop.

I tried to look for a key to disable the right-clcik menu, but I couldn't find any.

But depending on what you are trying to do, Gnome's lockdown editor, Pessulus, might be something you should check.. [http://www.linux.com/feature/62060]("http://www.linux.com/feature/62060") Also there's Sabayon, used to manage desktops settings for different users: [http://www.gnome.org/projects/sabayon/]("http://www.gnome.org/projects/sabayon/"). [http://www.gnome.org/~seth/blog/sabayon]("http://www.gnome.org/~seth/blog/sabayon")

---

### Post by lsutiger on 2008-08-27
Thanx, but I am already hitting walls with dependencies... there are 2 packages needed that I can not find in the repositories.
pygtk-2.0 and gnome-python-2.0.

---

### Post by mcduck on 2008-08-27
> **lsutiger said:**
> Thanx, but I am already hitting walls with dependencies... there are 2 packages needed that I can not find in the repositories.
pygtk-2.0 and gnome-python-2.0.

Both Pessulus and Sabayon are in ubuntu's repositories. Install them with Ubuntu's package management tools and you shouldn't need to worry about dependencies. ;)

---

### Post by lsutiger on 2008-08-27
Appreciate the help!

Neither one of those programs can do what I need (Disable right click on desktop or disable Create a Launcher on desktop). I have everything else locked down, I just need that one step and I am done.

---

### Post by PTo on 2008-08-29
I'm trying sabayon as well. However I don't get the result I want. When I run the editor, I loch many things down by lockdown editor, I put new icons on the desktop an change the desktop background. However when I log in on the user on which it applies, I only find the icons on the desktop. The other changes aren't made (nothing is locked down en the background hasn't changed). I have saved it though.

Anyone knows why this happens?

---

### Post by PTo on 2008-08-29
Some additional info:

When I quit profile editor it says: Sabayon will now exit.  There were some recoverable errors, and you can help us debug the problem by sending the log in /root/sabayon-debug-log.conf to [http://bugzilla.gnome.org](http://bugzilla.gnome.org)

This is what is written in the log:

===== BEGIN MILESTONES (/usr/bin/sabayon) =====
MainThread 2008/08/29 18:46:45.1783 (admin-tool): Creating profiles dialog
MainThread 2008/08/29 18:46:45.5687 (admin-tool): Starting main loop
MainThread 2008/08/29 18:49:44.2872 (admin-tool): sabayon-session exited normally
MainThread 2008/08/29 18:56:33.2604 (admin-tool): Got recoverable error: sabayon-session exited with RECOVERABLE exit status
MainThread 2008/08/29 18:56:48.7400 (admin-tool): Terminating main loop
MainThread 2008/08/29 18:56:48.7402 (admin-tool): Exiting normally; dumping log due to a recoverable error
===== END MILESTONES (/usr/bin/sabayon) =====
===== BEGIN RING BUFFER (/usr/bin/sabayon) =====
MainThread 2008/08/29 18:46:45.1783 (admin-tool): Creating profiles dialog
MainThread 2008/08/29 18:46:45.5687 (admin-tool): Starting main loop
MainThread 2008/08/29 18:46:48.8663 (USER): Starting to edit profile 'Test'
MainThread 2008/08/29 18:49:44.2872 (admin-tool): sabayon-session exited normally
MainThread 2008/08/29 18:49:53.4013 (USER): Finishing editing profile
MainThread 2008/08/29 18:50:25.8242 (USER): Starting to edit profile 'Test'
MainThread 2008/08/29 18:56:33.2604 (admin-tool): Got recoverable error: sabayon-session exited with RECOVERABLE exit status
MainThread 2008/08/29 18:56:37.9470 (USER): Finishing editing profile
MainThread 2008/08/29 18:56:48.7400 (admin-tool): Terminating main loop
MainThread 2008/08/29 18:56:48.7402 (admin-tool): Exiting normally; dumping log due to a recoverable error
===== END RING BUFFER (/usr/bin/sabayon) =====


This configuration for the debug log can be re-created
by putting the following in /root/sabayon-debug-log.conf
(use ';' to separate domain names):

[debug log]
max lines = 1000

---

