---
title: "Problem running Xgl for Beryl"
date: 2007-04-13
forum: Desktop Effects &amp; Customization
---

### Post by Bob Unitt on 2007-04-13
I'm on ubuntu edgy and want to try out Beryl, but I can't get my system to run an xgl session.

This PC is a 'hand-me-down', so I'm not sure exactly what the hardware is, but it's all fairly recent stuff. 

The video card describes itself as a 'VIA/S3G Unichrome IGP'. Running 'glxinfo | grep direct' returns 'direct rendering: Yes', and 'glxgears' runs OK apart from a warning that 'libGL warning: 3D driver claims to not support visual 0x46'.

I've followed the instructions in <http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl>  as far as possible, and tried the various forms of 'startxgl.sh' therein, but I always end up with the following when trying to log-on an Xgl session:-

I get a blank screen for a while, followed by a message box starting "Your session only lasted less than 10 seconds..." and containing :

[FONT="Courier New"]
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp
/etc/gdm/Xsession: Beginning session setup...
libGL warning: 3D driver claims not to support visual 0x46

_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal Server Error:
Cannot establish any listening sockets - Make sure an X-server isn't already running

(gnome session:11081) Gtk-WARNING** cannot open display
[/FONT]

The corresponding '.xsession_errors' file contains :

[FONT="Courier New"]
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp
 -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bobunitt"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Ubuntu:/tmp/.ICE-unix/10573

** (gnome-session:10573): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
evolution-alarm-notify-Message: Setting timeout for 31025 1176508800 1176477775
evolution-alarm-notify-Message:  Sat Apr 14 01:00:00 2007

evolution-alarm-notify-Message:  Fri Apr 13 16:22:55 2007

(gnome-panel:10643): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
[/FONT]

I'm out of my depth here - any help would be greatly appreciated...

---

### Post by ajmorris on 2007-04-14
It looks as though your hardware does not support XGL. Have you tried beryl with AIGLX instead? (it will run a lot faster if you use AIGLX instead of XGL)

(the instructions for AIGLX is on the same site as XGL instructions)

---

### Post by rabid9797 on 2007-04-14
i agree with aj on this one, VIA hardware is usually onboard(im assuming yours is), and if this is an older computer, which "hand-me-downs" usually are, they can't support XGL and the like. plus, XGL and beryl are incredibley resource consuming programs, and would most likley slow your computer down alot.

so i would suggest aiglx, much less resource consuming and easier with stress on your video, plus its supported more for older systems.

---

### Post by Bob Unitt on 2007-04-14
> **ajmorris said:**
> It looks as though your hardware does not support XGL. Have you tried beryl with AIGLX instead? (it will run a lot faster if you use AIGLX instead of XGL)

Thanks. I've de-installed XGL and activated AIGLX instead, as instructed by <https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy> but it hasn't made that much difference.

When I run 'BERYL --replace &' I get the following output in the terminal window :-
[FONT="Courier New"]
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x46
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
libGL warning: 3D driver claims to not support visual 0x46
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
[/FONT]

And the top and bottom panels of the screen disappear, along with the window borders and buttons on any applications I run.

This is getting more than a little frustrating - I think I need to chill for a while...

---

### Post by K.Mandla on 2007-04-14
(Moved to Desktop Effects.)

---

### Post by Bob Unitt on 2007-04-14
> **K.Mandla said:**
> (Moved to Desktop Effects.)

Thanks - I'll find my way round these forums (fora ?) eventually...

---

