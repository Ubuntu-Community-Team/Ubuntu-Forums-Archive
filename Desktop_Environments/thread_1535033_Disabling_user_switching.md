---
title: "Disabling user switching"
date: 2010-07-20
forum: Desktop Environments
---

### Post by N-t-F on 2010-07-20
Hello everyone ! :)

I've managed to get rid of the "hibernate" and "suspend" options using the procedure described here: [http://ubuntuforums.org/showthread.php?t=1477500](http://ubuntuforums.org/showthread.php?t=1477500). I also eliminated screen locking using gconf-editor.

I am now looking for a way to get rid of the fast-user switching. I have already removed the applet, but the option now appears in the "System" menu. Basically, I don't want users to have any other option than reboot, shutdown or disconnect from their session: no lock, no switch and no way to suspend the system, whatsoever.

I'm still a little concerned, by the way, that those methods only remove a few ways to access such functionalities rather than the functionalities themselves. If there were a few packages to uninstall to get rid of these, that would be awesome (except if it wrecked havoc in the OS, of course :mrgreen:)

Oh, and in case it might be of interest: the context is a bunch of classroom computers. Having someone locking a session, for instance, in such an environment is really annoying because other users need the administrator's help to unlock the system and use it.

---

### Post by mcduck on 2010-07-20
You can disable user switching through gconf. Just enable the desktop/gnome/lockdown/disable_user_switching -key.

You'll find couple of other useful locking options in the same place, like disabling print setup and command line access.

Also note that you might want to set mandatory values for these keys to make sure the user's can't just switch them back. Just run gconf-editor as root and use the "Set as Mandatory"-option from the right-click menu on any key.

If you want a more refined tool for managing such user settings, check out Pessulus (lockdown editor for Gnome) and Sabayon (used for creating and managing desktop settings for users/groups).

What comes to uninstalling components responsible of this kind of features versus disabling user's access to them, unistalling such core features wouldn't really be practical, and in the end it really makes no difference. The only tools that a normal, unprivileged user can use to suspend the machine or switch users etc. *are* the graphical ones on the desktop. They are rather special exceptions to the basic Unix system where a normal user doesn't have such permissions, so any command-line tool, for example, actually requires additional privileges. Normal user's simply can't use them. (For example GDM specifically allows a normal user to shut down the machine from the desktop, while the shutdown command in terminal requires root privileges.)

---

### Post by N-t-F on 2010-07-21
Thank you !

[QUOTE=mcduck]Also note that you might want to set mandatory values for these keys to make sure the user's can't just switch them back. Just run gconf-editor as root and use the "Set as Mandatory"-option from the right-click menu on any key.[/QUOTE]
Yes, I have done just that already, but the System menu still displays the option to switch users (and it's not just cosmetic: I've successfully tried it).

By the way and speaking about mandatory settings, it may be useful to some readers to know that they can't be set back to regular status from gconf-editor, apparently. You have to edit /etc/gconf/gconf.xml.default/%gconf-tree.xml or /etc/gconf/gconf.xml.mandatory/%gconf-tree.xml. Took me a grep command to figure this out. :p

[QUOTE=mcduck]If you want a more refined tool for managing such user settings, check out Pessulus (lockdown editor for Gnome) and Sabayon (used for creating and managing desktop settings for users/groups).[/QUOTE]I have dire memories of Sabayon, which caused me nightmares back when I configured Hardy Heron. But I guess it has evolved since then, and I will give Pessulus a try.

[QUOTE=mcduck]What comes to uninstalling components responsible of this kind of features versus disabling user's access to them, unistalling such core features wouldn't really be practical, and in the end it really makes no difference. The only tools that a normal, unprivileged user can use to suspend the machine or switch users etc. *are* the graphical ones on the desktop. They are rather special exceptions to the basic Unix system where a normal user doesn't have such permissions, so any command-line tool, for example, actually requires additional privileges. Normal user's simply can't use them. (For example GDM specifically allows a normal user to shut down the machine from the desktop, while the shutdown command in terminal requires root privileges.)[/QUOTE]Indeed, I guess that uninstalling packages in this case would be a little like using a sledgehammer to crack a nut and I know that /sbin/halt and such other commands are restricted to privileged users. My concern is precisely toward graphical ways to access them, as in the case of an option disappearing from the applets only to silently pop-up into the System menu.

Thank you anyway, I'll give another shot at gconf-editor to check that  have not overlooked a key, and try Pessulus. :)

---

### Post by mcduck on 2010-07-21
> **N-t-F said:**
> t).

By the way and speaking about mandatory settings, it may be useful to some readers to know that they can't be set back to regular status from gconf-editor, apparently. You have to edit /etc/gconf/gconf.xml.default/%gconf-tree.xml or /etc/gconf/gconf.xml.mandatory/%gconf-tree.xml. Took me a grep command to figure this out. :p

Actually they can, you just need to run gconf-editor as root and then select File/New Mandatory Window. From there you can remove the mandatory status from a setting. (same applies for default settings, File/New Defaults Window when running gconf-editor as root).

what cones to these settings not working, you must indeed be overlooking some setting or doing something otherwise wrong, as I just tried all of them and they work just fine.

---

### Post by N-t-F on 2010-07-21
[QUOTE=mcduck]Actually they can, you just need to run gconf-editor as root and then select File/New Mandatory Window. From there you can remove the mandatory status from a setting. (same applies for default settings, File/New Defaults Window when running gconf-editor as root).[/QUOTE]:oops: Indeed.

[QUOTE=mcduck]what cones to these settings not working, you must indeed be overlooking some setting or doing something otherwise wrong, as I just tried all of them and they work just fine.[/QUOTE]Well, I have set these:

/apps/gdm/simple-greeter/disable_user_list : true : mandatory
/apps/gnome-power-manager/actions/sleep_type_ac : nothing : mandatory
Everything in /apps/gnome-power-manager/lock/ : false : mandatory
/apps/gnome-screensaver/lock_enabled : false : mandatory
/apps/gnome-screensaver/user_switch_enabled : false : mandatory
/apps/panel/default_setup/general/applet_id_list : removed indicator-applet and fast_user_switch : default
/desktop/gnome/lockdown/disable_lock_screen : true : mandatory
/desktop/gnome/lockdown/disable_user_switching : true : mandatory
/desktop/gnome/session/idle_delay : 10 : default
/desktop/gnome/thumbnail_cache/maximum_size : 5 : default

And the menu "System" -> "Close session..." (not sure it is labeled exactly like that since I don't have an English environment) still displays both "Close session" and "Switch user" options.

I wonder if it may have something to do with the fact that I previously uninstalled indicator-me, indicator-messages and indicator-session. After all, some options automatically go into the system menu when you remove applets from the panel. I'll test that in the afternoon (well, I mean within a few hours) and report back.

---

### Post by N-t-F on 2010-07-21
Okay, I've tried to apply these settings over a fresh install I had to do anyway. As I suspected in my last post, applying them while the applets are all active result, as you mentioned, in a clean System menu and a session applet containing only the three options I want. This is perfect.

Now, I'll just have to uninstall network-manager and disable unwanted applets (that is most of them) without messing up things. But I guess the applets don't really need to be uninstalled since it is probably possible to disable them through Pessulus without causing havoc.

Thanks again for your help. :)

---

### Post by mcduck on 2010-07-21
No problem, and great that you got it sorted out.

By the way, you don't need to uninstall panel applets, the panel configuration can be locked down through gconf, which removes all the options for adding, removing, moving or configuring panel applets (or panels).

The gconf key for this is apps/panel/global/locked_down.

---

### Post by N-t-F on 2010-07-23
The issue is not entirely settled, after all. But I have found the culprit, that is indicator-applet. The option to switch users pops-up into the system menu as soon as I remove the indicator-applet from the panel. An alternative would be to find out how to remove everything from indicator-applet except the button used to halt, reboot and log out.

It also appears in any case into the log-out button menu if users access it, which means I will indeed have to lock the panel to prevent users from modifying it. Locking the panel won't solve the indicator-applet issue, though.

I do really miss a way to prevent user-switching at a system-wide level. :-\

I'm browsing through launchpad and will update this thread if I find something useful.

Okay, I just uninstalled indicator-me and everything seems ok. Hoping I won't have to open this thread again. ^^

---

