---
title: "beagled :("
date: 2006-08-20
forum: Desktop Environments
---

### Post by ESPOiG on 2006-08-20
first of all, i installed beagle found something on the web that told me to add this command to my fstab and then tried running beagle i got an error msg and so i check the log this is what i got. it said another instance was running, so i ctrl-alt-backspace and tried to no avail, then i rebooted still to no avail so now im asking for help :D...

this is the log

060820 2052253003 14154 Beagle DEBUG: Starting Beagle Daemon (version 0.2.6)
060820 2052253233 14154 Beagle DEBUG: Running on Mono 1.1.13.6
060820 2052253238 14154 Beagle DEBUG: Command Line: /usr/lib/beagle/BeagleDaemon.exe --bg
060820 2052253590 14154 Beagle DEBUG: Established a connection to the X server
060820 2052253605 14154 Beagle DEBUG: Starting main loop
060820 2052253675 14154 Beagle DEBUG: Starting messaging server
060820 2052254159 14154 Beagle ERROR: Could not set up the listener for beagle requests.  There is probably another beagled instance running.  Use --replace to replace the running service

ty in advance

---

### Post by lupine_nickt on 2006-08-20
In a terminal, try 'sudo killall -9 beagled' -- that terminates (with extreme prejudice) all running instances of the Beagle Daemon. 

Ctrl+Alt+Bkspace just kills the x-server (plus all apps depending on it), so won't do anything to non-graphical applications (i.e. almost all daemons).

To check with applications are running on your computer, run 'sudo ps aux'; if you're looking for a particular process, pipe the output to grep (e.g. 'sudo ps aux |grep <programname>') - note that you'll always find the 'grep' process, as well as any others that might be running.

HTH.

xF,

...Nick

Ooops, just read the error message properly. Before you do any of the above, try doing what it asks - ```

060820 2052254159 14154 Beagle ERROR: Could not set up the listener for beagle requests. There is probably another beagled instance running. Use --replace to replace the running service
```

So in a terminal, run 'beagle --replace' (optionally beagle --replace &', so that you can close the terminal window without closing beagle as well!)

---

### Post by ESPOiG on 2006-08-20
ok so i didnt read it properly and wasnt entirely sure wat i was doing there... but doing a --replace i did do and it still didnt work...

ive tried again but it still fails no beagle at all... except for the beagled  process running

no gui or anything so yeh

---

