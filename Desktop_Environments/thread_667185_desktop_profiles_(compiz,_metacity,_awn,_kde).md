---
title: "desktop profiles (compiz, metacity, awn, kde)"
date: 2008-01-14
forum: Desktop Environments
---

### Post by sexus6 on 2008-01-14
I want to know if is possible to make any kind of complete desktop profiles for a one single user.

This profiles that I want is for total customization of my desktop. For example, I want to create this profiles:

1.- Profile COMPIZ_GNOME = this profile I want that starts my gnome desktop,  with avant window navigator task bar (without the normal gnome taskbar) loaded, some screenlets on the desktop, emerald with one specific theme, one specific wallpaper, one specific fonts, icons etc....
2.- Profile METACIY_GNOME = this profile, I want that starts my gnome desktop, without avant, and the gnome panel to be task bar, some normal icons at the desktop (any screenlet, may be gdesklets), one specific  metacity theme, one specific wallpaper (different than the COMPIZ_GNOME profile) fonts, icons, etc.
3.- Profile METACITY_KDE = the same that the last profile, and JKDEdesktop....

I want to make this profiles, and switching them in real time (if is possible, don't exit to the GDM, like fusion-icon makes to swith between compiz and metacity).....

is this possible? HOW?

---

### Post by jackflap on 2008-01-14
I should think that the way to do this is to create different user accounts for each profile.

So you have a user account for COMPIZ_GNOME, another for METACITY_GNOME, and another for METACITY_KDE.

I'm pretty sure they've included fast user switching in 7.10 (meaning, being able to change user without logging out, but starting a new session from within the first one), and if they havent, they will very soon. If you look at the top-taskbar of the default gnome, you'll see a username, if you click on this you should be able to switch users very easily.

This would however mean, that any open applications will not follow you to your new user after you switch profiles. Not very much you can do about this I don't think, although, the old apps should remain running in the old session which will stay in the background. I haven't tested, so can't be sure.

Also, not sure if you can have two different task bars & window managers on different accounts. I should think you can since the Linux users have been designed from the ground up to be independently customizeable. 

If not though, you should be able to run a log-in script exiting your task bar, and loading the new one, could be a little fiddly, but once up and running you'll love it even more :)

Alex

---

### Post by sexus6 on 2008-01-14
For me multiple users is not an option.

I don't want to change user and lost opened programs. the main idea is that works like fusion-icon, but changing full desktop customized in real time...

Tthe gnome=>kde transision I know that would be difficult or imposible, but changing in real time icons+theme+taskbar+window manager (compiz or metacity)+windows decorator(emerald or GTK).....this is the idea. The main concept will be creating profile files that specify all the things loaded in each profile:

-COMPIZ
-EMERALD
-AWN
-Icons 

There is not any sollution to multiple desktop profiles for one user?

---

### Post by jackflap on 2008-01-14
To be honest, I'm pretty sure Ubuntu doesn't have any feature like this.

However, you could come up with a solution on your own. True, the KDE problem wouldnt work, but generally most configuration in Gnome is stored in the gconf, which can be edited using the command-line (using gconftool-2).

So it should be possible, to come up with some scripts which when run, would modify your running settings, so that they act kind of like profiles.

For instance, you can probably change the wallpaper using gconf (run gconf-editor and search through it to see what is currently configured), then using gconftool-2, you can probably update that setting from the command-line. Put the command required into a script, drop that script onto your desktop or something, then when you double-click it, the wallpaper should change.

Note. I've never actually done the wallpaper example, but I've done other things, like screensaver or power management settings, and it should work in the same way.

Then for other things, like the window manager, you could kill the current one, and load the new one from the command line again. So, with a bit of research, patience, you should be able to throw something together.

Alex

---

### Post by sexus6 on 2008-01-14
This idea starts with this posibility 
[http://ubuntuforums.org/showthread.php?t=667283]("http://ubuntuforums.org/showthread.php?t=667283")
that makes to use AWN with compiz, and when metacity is changed, taskbar panel would be showed, to change window tasksbar.

I expanded the idea with this desktop profiles, but I think that I was so far.

What about swtiching only  taskbar programs, gnome panels, icons, gtk theme, and wallpaper (kde or gnome remains)? Wich are the shell orders to make show or kill this panels or refresh this changes?

---

