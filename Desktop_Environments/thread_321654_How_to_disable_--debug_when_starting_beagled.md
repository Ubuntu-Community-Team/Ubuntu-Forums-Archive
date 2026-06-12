---
title: "How to disable --debug when starting beagled?"
date: 2006-12-19
forum: Desktop Environments
---

### Post by riskable on 2006-12-19
I'm trying to cut down on space in my home directory and I noticed that the beagle daemon is saving quite a large number of log files with no apparent rotation.  Looking at the running process, beagled is in debug mode:

> riskable@tomo:~/.conf[/email]ig/autostart$ ps aux | grep beagled
riskable  5369  0.4  2.1 104964 44604 ?        Sl   08:43   0:17 beagled --debug /usr/lib/beagle/BeagleDaemon.exe --bg

In my Gnome sessions panel, I have it set to start "beagled" when I login, so I'm curious how "--debug /usr/lib/beagle/BeagleDaemon.exe --bg" is getting tacked on to the end of it.  How do I get rid of the "--debug" part (since beagled is working fine)?

I grepped and beagled (the irony) for files that contain both "beagled" and "debug" and have come up empty handed.  I also checked the files inside /etc/beagle--nothing there either.  I've also checked ~/.config/autostart (nothing), and I also checked:

/etc/xdg/autostart/beagled.desktop
...and...
/usr/share/automatix2/conf/beagled.desktop

Neither of which appear to be launching beagle with "--debug".  This is quite a mystery and I can't fathom where else such a configuration setting would be.  If it isn't in a file on my system, where the fsck is it?!?  SOMETHING must be calling beagled with --debug SOMEWHERE.

Any help with this would be greatly appreciated.

---

### Post by riskable on 2006-12-19
Aha!  I've found it...  I didn't realize that "/usr/bin/beagled" was actually a shell script (which I checked using the file command: "file /usr/bin/beagled").  Not only that, but it is configured to ALWAYS run with --debug enabled, which I assume is a bug.  Specifically, on line 104:

> CMDLINE="$BEAGLE_MONO_RUNTIME --debug $MONO_EXTRA_ARGS $TARGET_EXE $BEAGLED_ARGS $FGBG_ARG"

That is the command which is run by default if no other options are set.  Note that the script actually checks to see if it was launched with "--debug" and enables it if you so desired.  The fact that "--debug" is included on line 104 completely negates the whole point of checking to see if debugging is enabled...  and there's no way to disable it (outside of editing the script).

So here's how I fixed it:  I removed "--debug" from line 104 and voila, beagled now runs without debugging.  Here's the documented process:

> riskable@tomo:~/.beagle/Log$ sudo vi /usr/bin/beagled
(fix line 104)
riskable@tomo:~/.beagle/Log$ ps aux | grep beagle
riskable  8882  1.6  2.4 106392 49980 pts/4    Sl   10:04   0:12 beagled --debug /usr/lib/beagle/BeagleDaemon.exe --bg
riskable  8945  0.4  1.3  69476 27428 pts/4    Sl   10:05   0:03 beagled-helper --debug /usr/lib/beagle/IndexHelper.exe
riskable  9314  0.0  0.0   2796   764 pts/4    R+   10:17   0:00 grep --color beagle
riskable@tomo:~/.beagle/Log$ killall beagled
riskable@tomo:~/.beagle/Log$ ps aux | grep beagle
riskable  9321  0.0  0.0   2800   764 pts/4    R+   10:17   0:00 grep --color beagle
riskable@tomo:~/.beagle/Log$ beagled
riskable@tomo:~/.beagle/Log$ ps aux | grep beagled
riskable  9325 13.1  0.9  56620 19300 pts/4    Sl   10:17   0:00 beagled /usr/lib/beagle/BeagleDaemon.exe --bg
riskable  9339  0.0  0.0   2796   760 pts/4    R+   10:17   0:00 grep --color beagled

I am going to submit the bug report now.

---

### Post by riskable on 2006-12-19
I have updated an existing bug:  [https://launchpad.net/distros/ubuntu/+source/beagle/+bug/64807]("https://launchpad.net/distros/ubuntu/+source/beagle/+bug/64807")

...not sure why it is listed as fixed when it clearly isn't.  If you don't want to wait for the next release of beagle, just type the following into a terminal:

```
sudo sed -i -e '104s/--debug //' /usr/bin/beagled
```

That will fix the bug in the /usr/bin/beagled script

---

