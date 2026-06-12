---
title: "Unable to start GNOME: &quot;(process:5825): Gtk-WARNING **: This process [...]&quot;"
date: 2008-01-27
forum: Desktop Environments
---

### Post by elreteipos on 2008-01-27
When I try to start GNOME, I get this fatal error:> *[Note: I retrieved this information from ~/.xsession-errors.]*
(process:5825): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5829): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
session_child_run: kon /etc/gdm/Xsession /usr/bin/gnome-session niet uitvoerengdm[5822]: WARNING: session_child_run: kon /etc/gdm/Xsession /usr/bin/gnome-session niet uitvoeren

Now, I have messed around with /etc/gdm/Xsession a little bit. I've added something to the bottom of the file and then removed that section. Here's what the bottom looks like:> [...]
echo "$0: Executing $command failed, will try to run x-terminal-emulator"

if [ -n "$zenity" ] ; then
        "$zenity" --info --text "`gettextfunc "I could not start your session and so I have started the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upper left corner"`"
fi

exec x-terminal-emulator -geometry 80x24+0+0
GNOME Safe Mode is working just fine.

---

### Post by elreteipos on 2008-01-30
Update: found an old Xsession backup with the VNC code at the bottom. Here's the bottom of the file:> if [ -n "$zenity" ] ; then
        "$zenity" --info --text "`gettextfunc "I could not start your session and so I have started the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upper left corner"`"
fi

exec x-terminal-emulator -geometry 80x24+0+0

xhost +localhost
killall x11vnc &>/dev/null
x11vnc -rfbauth /home/pdedecker/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -scale 4/5 -scale_cursor 1 -desktop BETAubuntu -bgAssuming that this version of Xsession still worked, the current Xsession file is not broken. What else could be wrong?

---

