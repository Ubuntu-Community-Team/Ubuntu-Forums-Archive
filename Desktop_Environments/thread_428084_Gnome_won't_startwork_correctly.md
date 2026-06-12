---
title: "Gnome won't start/work correctly"
date: 2007-04-30
forum: Desktop Environments
---

### Post by Omegatron on 2007-04-30
I was rotating something in Inkscape and my whole system locked up.  It was just scrubbing away at the hard drive and not responding at all for 15 minutes or so, so I forced the computer to shut down.

When I restarted, Gnome doesn't work.  When I first try to log in, it gives the splash screen, starts to load, and then turns black and goes back to the login screen.  If I log in a second time, it works, but it pops up a window saying:

> 
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.


If I press Ok on that window, everything crashes.  If I ignore the window and just let it sit there, everything runs relatively normally.  It doesn't remember my network-manager password, though, and asks for it.

If, instead, I run Gnome failsafe, everything works fine and instead of asking me for the WPA password, it asks for the keyring password, which is what it's supposed to do.

I have 3 GB free.  The ~/.ICEauthoriity file is owned by me, and I didn't install K3B.  The window that pops up says that this is the contents of:

"View details (~/.xsession-errors file):"
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "omegatron"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Inspiron:/tmp/.ICE-unix/5687
Initializing gnome-mount extension

(update-notifier:5756): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:5771): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:5772): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:5774): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:5768): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

I tried removing ~/.gnome2/session and ~/.gconfd/saved_state, but they don't fix it.  At  one point it would start gnome but complain that gnome-panel was already started and not display the panel.  Other times it would not start the window manager, and I had to type in metacity by hand.  Deleting those hidden files maybe fixed these two problems?  It's hard to tell.

---

### Post by Omegatron on 2007-04-30
GNOME failsafe works fine, but GNOME session and "Run Xclient script" do not.  Can anyone explain what's different about these options?  I can't find any explanation of what "Run Xclient script" means or why it's the default.

---

### Post by Omegatron on 2007-04-30
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "omegatron"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Inspiron:/tmp/.ICE-unix/6570
Initializing gnome-mount extension

** (gsynaptics-init:6667): WARNING **: Using synclient
** Message: failed to load session from /home/omegatron/.nautilus/saved-session-OIQLRT

(gnome-panel:6634): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 25

```

---

### Post by ellisdee on 2007-04-30
hrmm I too have the same problem with

> (update-notifier:5756): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:5771): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:5772): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:5774): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:5768): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

and with the same scenario

> 
At one point it would start gnome but complain that gnome-panel was already started and not display the panel. Other times it would not start the window manager


I'm using KDE in the interim as I don't have the time to fix it while at work :(

---

### Post by ryankhart on 2007-05-03
I did a google search for an answer to this exact same problem hoping to get an answer. Sorry, I'm in the same position. We have identical problems.

My only thought would be that we are low on disk space. I've only got 6 GB left and you've only got 3 you said. Can any experts please tell us how to delete/remove programs and files (from trash as well) from the terminal?

---

### Post by Omegatron on 2007-05-03
> **ryankhart said:**
> My only thought would be that we are low on disk space. I've only got 6 GB left and you've only got 3 you said.

I'm sure that's not the problem.  You don't start having problems until you get down to a few hundred MB. 

If you switch sessions to GNOME Failsafe, does it work?

---

### Post by randlieb on 2007-05-03
i had similar problem with logging in. i would get the 'session ten second...blah blah blah' message and would get to my desktop but if i closed the error window it would throw me back to log-in screen. if i didn't close the error window all would work ok except when i clicked on the log out icon in the panel the screen went blank and i was back at the log-in screen. while in the wiggy session i was unable to open session manager.

and i have PLENTY of disc space so that's not the issue with me.

did you install gnome art manager? and then change image in splash screen manager?

 thought it might have something to do with the above (it was the last change i made to the system before it went all wiggy on me). 

i logged into failsafe mode and un-installed gnome art and took out the new image in splash screen manager and disabled splash screen.

i re-booted and logged back in to xclient session and everything seems to be working now. if anything pops up again i'll post here.

---

### Post by Omegatron on 2007-05-03
> **randlieb said:**
> i had similar problem with logging in. i would get the 'session ten second...blah blah blah' message and would get to my desktop but if i closed the error window it would throw me back to log-in screen. if i didn't close the error window all would work ok except when i clicked on the log out icon in the panel the screen went blank and i was back at the log-in screen. while in the wiggy session i was unable to open session manager.

Exactly the same behavior.  We should file a bug report, I guess.  But I also want to fix it.

> did you install gnome art manager? and then change image in splash screen manager?

I have changed the splash screen from System-->Preferences, but I do not have a program called gnome-art-manager.

I had no problems with a custom splash screen, though.  My problems started after my computer locked up and I shut it down by holding down the power button.  (I probably should have tried Ctrl-Alt-F1 first and told it to shutdown from the command line, but I forgot you can do that.)  No other key commands were registering anyway.

> i logged into failsafe mode and un-installed gnome art and took out the new image in splash screen manager and disabled splash screen.

Interesting...

---

### Post by Krymzon on 2007-05-10
I've got a similar problem and can't fix it yet&#8230; :(
Using failsafe gnome for the third day.

I don't remember changing anything particular in the system before it started.

---

### Post by Endolith on 2007-05-10
> **Krymzon said:**
> I've got a similar problem and can't fix it yet… :(
Using failsafe gnome for the third day.

I don't remember changing anything particular in the system before it started.

what error message?

---

### Post by Krymzon on 2007-05-10
Wow, I turned the gnome splash off and now I can log in normally!:)
AFAIR I haven't changed the splash screen for months, it appears a package update somehow conflicts with it.

[edit]It doesn't appear to be a problem of any particular splash screen, but of the program itself

---

### Post by Omegatron on 2007-05-10
> **Krymzon said:**
> Wow, I turned the gnome splash off and now I can log in normally!:)
AFAIR I haven't changed the splash screen for months, it appears a package update somehow conflicts with it.

[edit]It doesn't appear to be a problem of any particular splash screen, but of the program itself

Did you also get the message saying your session lasted less than 10 seconds?  And if you push OK it would crash?

---

### Post by Krymzon on 2007-05-11
Yes.

With splash turned off everything keeps on working now :)

---

### Post by Omegatron on 2007-05-13
> **Krymzon said:**
> Yes.

With splash turned off everything keeps on working now :)

What do you mean "with splash turned off"?  I uninstalled gnome-splash-manager and it did nothing.  Still no window manager in the default session.

---

### Post by Krymzon on 2007-05-14
System>Preferences>Splash Screen (I guess that's gnome-splash-manager)
Uncheck "Show splash screen on startup"

---

### Post by janformanek on 2007-05-16
> **Krymzon said:**
> System>Preferences>Splash Screen (I guess that's gnome-splash-manager)
Uncheck "Show splash screen on startup"

The name is gnome-splashscreen-manager and before you remove it make sure you uncheck splash screen as described above. Worked for me :)

---

### Post by Omegatron on 2007-05-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The fix for bug 106350 seems to have fixed this, too.

---

### Post by tom72 on 2007-05-26
I had the same problem. I have Beryl running and it does start at the beginning, however after a few seconds the window decorators disappear and the dreaded message from above appears.
I fixed it this way:

moved all *.desktop files from ~/.config/autostart  to a different location
after logging in again to X it all went smooth
unchecked the "show_splash_screen" checkbox in the gconf editor (key under: apps -> gnome-session -> options)
moved all the *.desktop files to the original location again and logged in again, everything worked now except that the splash screen is not shown anymore

---

