---
title: "Firefox : &quot;Couldn't load XRE functions.&quot;"
date: 2009-06-23
forum: General Help
---

### Post by jdb2 on 2009-06-23
I'm running Kubuntu 9.04/Jaunty with KDE 4.3 Beta 2. Before the problem described below started, I was running off of an external USB 500GB hard drive. I needed more space so I bought an external eSATA-II 1TB hard drive and ran the proverbial "cp --no-dereference --preserve=all -R -v ..." in order to transfer my data to the new drive -- Note that I have had no problems with this in the past. After updating the UUIDs in GRUB's menu.lst and in /etc/fstab, re-grubbing the drive and marking it bootable, I successfully booted up with no apparent problems -- that is, until I tried to launch Firefox. Attempting to launch Firefox, which was then at version 3.0.10, from the KDE panel or menu resulted in just the bobbing Firefox icon which stopped after a few seconds only to leave a Firefox tab in the panel which then disappeared. Repeated attempts to launch Firefox always resulted in Plasma crashing. Attempting to run it from the console produced "Couldn't load XRE functions." and attempting to run GDB with the '--debug' option produced the following output or similar :

```
jdb2@jdb2-Kubuntu-temp:~$ firefox --debug
/usr/bin/gdb /usr/lib/firefox-3.0.10/firefox -x /tmp/mozargs.PaJJIv
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(no debugging symbols found)
(gdb) run
Starting program: /usr/lib/firefox-3.0.10/firefox
[Thread debugging using libthread_db enabled]
[New Thread 0xb7daf6d0 (LWP 15070)]
Couldn't load XRE functions.

Program exited with code 01.
(gdb) 

```

( It's interesting to note that the above reports that no debugging symbols were found even though I have the ddebs installed for Firefox 3.0.10/11/5/6 as well as all the components listed [here](https://wiki.ubuntu.com/MozillaTeam/Bugs#Obtain%20a%20backtrace%20from%20an%20apport%20crash%20report%20%28using%20gdb%29)  )


All the above applies, without any apparent changes, to my current install of Firefox 3.0.11 courtesy of an Ubuntu update.

I've compiled a debug build of Firefox 3.0.11 from an official Mozilla Project tarball, which works fine to my surprise as well as to my confusion. I've also tried deleting the profile directory ( after having backed it up ) which changes nothing. I've tried launching Firefox 3.5b4pre from the menu and panel which results in the same behavior as described concerning 3.0.10/11. Also, I've installed Firefox 3.6 from the ubuntu-mozilla-daily repository, but attempting to launch it results in the same behavior described above, although trying to run it from the console  -- 'firefox-3.6' -- produces no output -- there is only a slight pause upon which it exits back to the shell. 

The firefox-3.6 '--debug' output is somewhat different from that of 3.0.10/11 :

```

jdb2@jdb2-Kubuntu-temp:~$ firefox-3.6 --debug
/usr/bin/gdb /usr/lib/firefox-3.6a1pre/firefox-3.6 -x /tmp/mozargs.kQTcZN
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(no debugging symbols found)
(gdb) run
Starting program: /usr/lib/firefox-3.6a1pre/firefox-3.6
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c046d0 (LWP 19839)]
[New Thread 0xb52ffb90 (LWP 19842)]
[New Thread 0xb4afeb90 (LWP 19843)]
[New Thread 0xb3fffb90 (LWP 19846)]
[New Thread 0xb35ffb90 (LWP 19847)]
[Thread 0xb35ffb90 (LWP 19847) exited]
[New Thread 0xb35ffb90 (LWP 19848)]
[Thread 0xb52ffb90 (LWP 19842) exited]
[Thread 0xb35ffb90 (LWP 19848) exited]
[Thread 0xb3fffb90 (LWP 19846) exited]
[Thread 0xb4afeb90 (LWP 19843) exited]

Program exited with code 01.
(gdb)

```

Also, I've tried re-installing all of the above. The only thing that ***does*** work is running Firefox 3.5 from the console.

Does anyone have any idea about what might be going on?

Any help is appreciated.

jdb2

---

