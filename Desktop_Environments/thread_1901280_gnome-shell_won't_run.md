---
title: "gnome-shell won't run"
date: 2011-12-28
forum: Desktop Environments
---

### Post by jissouille on 2011-12-28
Hi, I want to try gnome-shell (Oneiric/64) but it does not run.
I created a new "test" user with blank home directory. 
There is no "gnome-shell" session name in gdm or lightdm (maybe that's normal ?)
When I log on "gnome" session, I get a (default) background and nothing more (right click shows a menu).
If I open a terminal (with Ctrl-Alt-T) and type gnome-shell --replace & I get :

```

test@bast:~$ gnome-shell --replace &
[1] 22824
test@bast:~$ Avertissement du gestionnaire de fenêtres : Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Avertissement du gestionnaire de fenêtres : Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Tue Dec 27 2011 01:34:49 GMT+0100 (CET)
Avertissement du gestionnaire de fenêtres : Log level 16: The program 'gnome-shell' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 734 error_code 8 request_code 7 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

gnome-shell-calendar-server[22832]: Got HUP on stdin - exiting

```Unity runs perfectly (nice oxymore) so it's not a 3D problem.
Since the home directory is empty it is not a shell extension problem.

[SIZE=2]**How can I see what "PolicyKit auth. agent" is being used and how can I remove it or prevent it from starting ?**[/SIZE]

I have tried installing cinnamon but same "Polkit auth agent" problem.

My main session runs compiz+cairo-dock to mimic menu/panel/tray (I'd rather switch back to windows rather than use unity)

Many thanks for your help, link, advice...

---

