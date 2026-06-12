---
title: "splashscreen change causes crash at login"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by KIAaze on 2007-05-27
I installed this splashscreen: [http://art.gnome.org/themes/splash_screens/1330]("http://art.gnome.org/themes/splash_screens/1330")

However, when I restarted and wanted to relogin, I couldn't.
The splash screen appeared as I wanted it too, but before the desktop was fully loaded, it suddenly crashed and went back to the login screen.
I had to disable the splashscreen to be able to log in again by calling  "gconf-editor /apps/gnome-session/options" from a terminal mode (even failsafe didn't work).

Here's the .xsession-errors file:

```
cat .xsession-errors

(process:10981): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:10985): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "yo"
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/default linked to /etc/X11/xinit/xinput.d/default.

***MEMORY-WARNING***: gnome-session[10977]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

***MEMORY-WARNING***: gconf-sanity-check-2[11026]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
SESSION_MANAGER=local/yo-laptop:/tmp/.ICE-unix/10977

** (process:11028): WARNING **: couldn't connect to dbus session bus: Failed to execute dbus-launch to autolaunch D-Bus session

***MEMORY-WARNING***: gconftool-2[11082]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

***MEMORY-WARNING***: metacity[11058]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Failed to read saved session file /home/yo/.metacity/sessions/default0.ms: Failed to open file '/home/yo/.metacity/sessions/default0.ms': No such file or directory
** Message: Not starting remote desktop server
Initializing gnome-mount extension

***MEMORY-WARNING***: gconftool-2[11098]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

***MEMORY-WARNING***: gconftool-2[11128]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
[: 99: ==: unexpected operator

***MEMORY-WARNING***: gconftool-2[11129]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

***MEMORY-WARNING***: gconftool-2[11130]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...
[: 99: ==: unexpected operator
modinfo: could not find module nvidia_new

(gnome-panel:11061): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing warnaltenter.ogg.
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 28.0 kbit/21.88% (ratio: 3500->16000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 8000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 1.2 (01.2)  0.1%
kdecore (KProcess): WARNING: _attachPty() 10

Exiting... (End of file)
  PID TTY          TIME CMD
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing warnalpdiscon.ogg.
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 28.0 kbit/21.88% (ratio: 3500->16000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 8000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 1.4 (01.4)  0.1%

Exiting... (End of file)
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing warnaltenter.ogg.
[Ogg] stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 8000 Hz, 1 ch, s16le, 28.0 kbit/21.88% (ratio: 3500->16000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
AO: [alsa] 8000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 1.2 (01.2)  0.1%

Exiting... (End of file)

***MEMORY-WARNING***: firefox-bin[11673]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

```

---

### Post by asymmetric on 2007-06-09
same here, i uninstalled gnome-art, gnome-splashscreen-manager and deleted everything under $HOME/.gnome2/gnome-art/download/

---

### Post by G@B0 on 2007-06-12
Thx guys u solved my problem.
In my case after isntalling a splash with gnome art manager it crashed and give me a black screen.

Now by disable the splash Im able to enter.
Now its time to delete all relationated with that just like asymmetric says.

Thx a lot.
BTW my post was here. [http://ubuntuforums.org/showthread.php?t=470341&highlight=art+manager](http://ubuntuforums.org/showthread.php?t=470341&highlight=art+manager)

---

