---
title: "gxine, totem, mplayer loads then shutsoff"
date: 2006-06-17
forum: Desktop Environments
---

### Post by wgs8453 on 2006-06-17
I am attempting to play to play dvds but gxine, totem, mplayer loads then shutsoff. What could be wrong???

Thanks,
wgs

---

### Post by weijie90 on 2006-06-17
what were the steps you took to > play dvds?

---

### Post by scxtt on 2006-06-17
try starting them from a terminal window and seeing if they provide you w/ any error messages ...

---

### Post by wgs8453 on 2006-06-18
[QUOTE=scxtt]try starting them from a terminal window and seeing if they provide you w/ any error messages ...[/QUOTE]

~$ gxine
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?  sysname: Linux
  release: 2.6.15-25-386
  machine: i686
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.  (Details: serial 451 error_code 11 request_code 140 minor_code 19)  (Note to programmers: normally, X errors are reported asynchronously;   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line   option to change this behavior. You can then get a meaningful   backtrace from your debugger if you break on the gdk_x_erro

That is what I got using terminal.

wgs8453

---

### Post by msandersen on 2006-06-30
I'm having a similar problem with a couple of apps. I installed gxine, but when I start it, the player comes up, followed by a first-play wizard. Once I click Forward, the button gets stuck in the Down position and freezes.
Starting from Terminal, I get:
```
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
  sysname: Linux
  release: 2.6.15-25-686
  machine: i686

```
 I don't get any warnings about X, though, unlike the above. I have been experimenting with the compmgr, but shutting it off doesn't make a difference. Maybe it's related to **System > Administration > Disks** freezing on startup, too. Totem works. Rhythmbox fails to run with no errors. On the terminal, just starts and stops.
gmplayer outputs the following:
> 91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).


---

### Post by dmizer on 2006-06-30
i have this exact same problem with totem:
```
$ totem
/bin/sh: /usr/bin/esd: &#12381;&#12398;&#12424;&#12358;&#12394;&#12501;&#12449;&#12452;&#12523;&#12420;&#12487;&#12451;&#12524;&#12463;&#12488;&#12522;&#12399;&#12354;&#12426;&#12414;&#12379;&#12435; (that file or directory does not exist)
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 69 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
it was working at one point.  you didn't happen to use easyubuntu did you?

---

### Post by syxbit on 2006-06-30
i have the same problem.
what's weird is that if i put in a DVD it autoplays and works perfectly.
if i just want to open totem by itself it opens and just closes itself after about 1 second.
i used Automatix (got a feeling that might be the problem)
any ideas ?

---

### Post by syxbit on 2006-07-02
i'm having problems with ALL dvd programs except KDE based ones, and it's making me really mad.
could this have anything to do with me having an ATI gfx card ?

---

