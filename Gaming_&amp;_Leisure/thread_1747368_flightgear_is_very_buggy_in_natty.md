---
title: "flightgear is very buggy in natty"
date: 2011-05-02
forum: Gaming &amp; Leisure
---

### Post by habib_seif on 2011-05-02
Hi all,

Unfortunately, flightgear worked only once on my computer (only when it was just installed). After that it could not load scenery objects (it only showed water when it started).

After installing some airports and choosing them from the menu, the scenery objects are loaded but no key works. I even cannot start engine or change flap.

Flightgear also prints a lot of errors when I start it from the command:


```


habib@habib-Inspiron-N4030:~$ fgfs 
FGMultiplayMgr - No receiver port, Multiplayermode disabled
Not overwriting write-protected property /sim[0]/fg-root
Not overwriting write-protected property /sim[0]/startup/browser-app
Not overwriting write-protected property /sim[0]/sound/voices/host
Not overwriting write-protected property /sim[0]/sound/voices/port
Not overwriting write-protected property /sim[0]/fg-home
Not overwriting write-protected property /sim[0]/fg-current
Nasal runtime error: foreach enumeration of non-vector
  at /usr/share/games/FlightGear/Nasal/view.nas, line 632
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 113
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Not overwriting write-protected property /instrumentation/mk-viii/outputs/discretes/gpws-warning
Not overwriting write-protected property /instrumentation/mk-viii/outputs/discretes/gpws-alert
Not overwriting write-protected property /instrumentation/mk-viii/outputs/discretes/audio-on
Not overwriting write-protected property /instrumentation/mk-viii/outputs/discretes/gpws-inop
Not overwriting write-protected property /instrumentation/mk-viii/outputs/discretes/tad-inop
Not overwriting write-protected property /instrumentation/mk-viii/outputs/discretes/flap-override
Not overwriting write-protected property /instrumentation/mk-viii/outputs/discretes/glideslope-cancel
Not overwriting write-protected property /instrumentation/mk-viii/outputs/discretes/steep-approach
Not overwriting write-protected property /instrumentation/mk-viii/outputs/arinc429/egpws-alert-discrete-1
Not overwriting write-protected property /instrumentation/mk-viii/outputs/arinc429/egpwc-logic-discretes
Not overwriting write-protected property /instrumentation/mk-viii/outputs/arinc429/mode6-callouts-discrete-1
Not overwriting write-protected property /instrumentation/mk-viii/outputs/arinc429/mode6-callouts-discrete-2
Not overwriting write-protected property /instrumentation/mk-viii/outputs/arinc429/egpws-alert-discrete-2
Not overwriting write-protected property /instrumentation/mk-viii/outputs/arinc429/egpwc-alert-discrete-3
Nasal runtime error: No such member: listener
  at /usr/share/games/FlightGear/Nasal/view.nas, line 342
  called from: /usr/share/games/FlightGear/Nasal/view.nas, line 228
  called from: /usr/share/games/FlightGear/Nasal/view.nas, line 218
  called from: /usr/share/games/FlightGear/Nasal/view.nas, line 626
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 202
  called from: /usr/share/games/FlightGear/Nasal/multiplayer.nas, line 378
  called from: /usr/share/games/FlightGear/Nasal/multiplayer.nas, line 446
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 202
  called from: /usr/share/games/FlightGear/Nasal/io.nas, line 210
Nasal runtime error: props.setAttribute() with invalid attribute
  at /usr/share/games/FlightGear/Nasal/props.nas, line 25
  called from: /usr/share/games/FlightGear/Nasal/gui.nas, line 137
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 202
  called from: /usr/share/games/FlightGear/Nasal/gui.nas, line 376
  called from: /usr/share/games/FlightGear/Nasal/aircraft.nas, line 519
  called from: /usr/share/games/FlightGear/Aircraft/c172p/Nasal/liveries.nas, line 3
KI266 dme indicator #0 initialized
loading scenario 'nimitz_demo'
creating 3D noise texture... ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
DONE
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Failed to load object 
Nasal runtime error: No such member: listener
  at /usr/share/games/FlightGear/Nasal/view.nas, line 342
  called from: /usr/share/games/FlightGear/Nasal/view.nas, line 228
  called from: /usr/share/games/FlightGear/Nasal/view.nas, line 218
  called from: /usr/share/games/FlightGear/Nasal/view.nas, line 655
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 113
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 113
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: bad/missing argument to subvec()
  at /usr/share/games/FlightGear/Nasal/string.nas, line 225
  called from: /usr/share/games/FlightGear/Nasal/string.nas, line 235
  called from: /usr/share/games/FlightGear/Nasal/failures.nas, line 99
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Nasal runtime error: No such member: list
  at /usr/share/games/FlightGear/Nasal/view.nas, line 357
  called from: /usr/share/games/FlightGear/Nasal/view.nas, line 345
  called from: /usr/share/games/FlightGear/Nasal/view.nas, line 239
  called from: /usr/share/games/FlightGear/Nasal/view.nas, line 159
  called from: /usr/share/games/FlightGear/Nasal/dynamic_view.nas, line 424
  called from: /usr/share/games/FlightGear/Nasal/dynamic_view.nas, line 433
  called from: /usr/share/games/FlightGear/Nasal/globals.nas, line 100
Initializing Nasal Electrical System
power up

```

I wonder if the error of non-functioning keys is related to the above errors but the it sounds that the flightgear is very buggy in this version of ubuntu.

Anyway, any help to solve the problem of keys is appreciated.

Sincerely,
Habib Seifzadeh

---

### Post by cigtoxdoc on 2011-05-02
Just installed flightgear under 11.04 using synaptic.  Program will not launch from Ubuntu Classic desktop.  Launch form command line gives:

john@landallc:~$ fgfs
Xlib:  extension "GLX" missing on display ":0.0".
Error: :0.0 has no GLX extension.
Xlib:  extension "GLX" missing on display ":0.0".
Error: :0.0 has no GLX extension.
Segmentation fault

What is ream of errors and how do I resolve them?

John

---

### Post by habib_seif on 2011-05-03
Another bug with flightgear in natty is its icon.
The Icon entry in the /usr/share/applications/flightgear.desktop has no value.

Cheers,
Habib

---

### Post by Martyn Thompson on 2011-06-19
Also having problems with flightgear. 

Got an X11ErrorHandling call display=0x99679d8 event=0xbfe6428c
BadRequest (invalid request code or no such operation)
Major opcode: 136
Minor opcode: 19
Error code: 1
Request serial: 15
Current serial: 15
  ResourceID: 23

and similar... 

Using Ubuntu 11.04

---

### Post by ericrules on 2011-07-08
I've just installed flightgear, and it keeps crashing just after it has loaded.  The aeroplane appears, and then it crashes about 10 seconds later.  Any ideas about how i can stop this?

---

