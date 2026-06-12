---
title: "Problem with Gnome and Compiz - Gutsy/Fiesty"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by shockwaver on 2007-10-23
Hey, I've looked around, installed compiz a few different ways. First via repo, then I tried to install 6.0 from source because I wanted to compile plugins (Never -did- get that working). When I had installed compiz via apt-get, things seemed to work ok for gnome. I removed the repo install, installed from source and compiz worked fine in gnome up until I rebooted.. But, oddly if I changed the Xgl script to call KDE, everything works fine - I just don't like KDE as much any more.

Now, to make things more difficult! I uninstalled the source install of compiz, and upgraded from fiesty to gutsy via the upgrade dialog box. Previously, I was able to enter gnome without the Xgl.. but after the upgrade, gnome just dies, giving me xsession-errors. I've copied it here. KDE+Xgl (my old Xgl .session script from the ubuntu wiki on installing compiz) still works fine.

```
(process:18635): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:18639): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
xmodmap:  unable to open display ':1'

(gnome-session:18632): Gtk-WARNING **: cannot open display:  
```

Now, this error is similiar to the one I was getting before I upgraded, but I don't believe it had the setuid error in the beginning. Any advice? I really want to use Gnome (much cleaner UI IMHO), but compiz with expose was really helping my productivity and frustration level.

Thanks in advance!

---

### Post by shockwaver on 2007-10-24
Minor update:

If I log in to the gnome failsafe, and use synaptic package manager to completely remove compiz and xgl, then reinsintall them both, I can log out and log back in to the regular gnome session that starts xgl just fine. I just can't log out or reboot without getting that message.

---

### Post by shockwaver on 2007-10-25
Any advice? I've added the ~/.config/xgl/disable file to stop it from starting up when I log in, so I can use the desktop, but I'd like to get things working again.

---

### Post by shockwaver on 2007-11-04
Is there anybody out there?

---

### Post by nemarasu on 2007-11-06
I'm getting the same error... Only I didn't use a custom compiz, i used the one provided via the package manager. I received an update notification that a few items were in need of upgrade (compiz), I rebooted and now its failing.

(process:5740): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5744): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/vostro:/tmp/.ICE-unix/5737

(gnome-volume-manager:5792): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

---

### Post by shockwaver on 2007-11-06
Well, I completely removed the from source install of compiz, and completely ('Remove Completely' using synaptic) removed xgl and several compiz type files, and reinstalled them so that I should (ideally? Hopefully? maybe?) be using a clean install of it, but still getting the same errors. I'm -thinking- the problem lies somewhere in the Xgl install, since it seems to be barfing when Xgl tries to start inside the gnome session.

---

### Post by nemarasu on 2007-11-06
I can't get a usable desktop at all.

---

### Post by shockwaver on 2007-11-06
Quick and dirty solution is to use 'Failsafe Gnome', and if for some reason that doesn't work, if you can get to a shell CTRL+ALT+F2, and add this file ~/.config/xserver-xgl/disable. CTRL+ALT+F7 brings you back to the gdm (Or, it does for me)

eg:
```
mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable
```

should let you use a standard gnome session without it trying to bring up Xgl. Doesn't solve the desktop effect issue, but does let you use your computer.

---

### Post by nemarasu on 2007-11-06
I can get to a shell, np there. But ever since a compiz update yesterday evening, gnome won't start properly w/o that error and  I'm getting a cupsys error. I also tried the /disable bit, but that isn't working either.

I'm backing up /home, I'm going to wipe/re-install, then update and see if it happens again.

---

### Post by shockwaver on 2007-11-06
I just tried something, that you might want to try. Or, moreso.. could you if you are going to wipe your computer? edit /etc/gdm/gdm.conf and find where it says
GdmXserverTimeout=10
and change it to say
GdmXserverTimeout=50
and remove the /disable file to see if it works.

I did this, restarted gdm (CTRL ALT BACKSPACE) and got in to my desktop, but it seemed to hang after it started loading some of my start up programs, so I restarted it again, and got the error. Incidentally, I couldn't get in to any of my sessions, failsafe or otherwise afterwards. Couldn't even get to a shell so I had to SSH from my laptop and add the disable file back. Maybe you'll have better results. I -hate- this Sony PoS with PoS ATI graphics. Damn thing won't even let me dual boot without breaking so it could be my hardware that is causing headaches.

---

### Post by nemarasu on 2007-11-07
Sorry, I nuked it right after posting... So here are the results.

Installed 7.10 (just as I did before, nothing special)

ran through the upgrades, installed some software that i use (doesn't interface with compiz/xgl/etc...), and it seems to be working fine.

I didn't have time last nite, but tonite I'll turn on more eye candy to see if that breaks it. Otherwise its working fine.

Sorry for not trying to troubleshoot it more, but I needed to do some work (*shudder*).

---

### Post by shockwaver on 2007-11-10
Don't suppose anyone has any ideas for help for this?

---

### Post by nemarasu on 2007-11-16
so I reinstalled, ran patches, upped the graphics, and it did NOT blow up on me this time. All the sames apps installed as before as well.

Sorry I could not replicate the issue.

---

