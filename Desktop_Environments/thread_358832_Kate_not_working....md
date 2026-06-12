---
title: "Kate not working..."
date: 2007-02-11
forum: Desktop Environments
---

### Post by MasterOfMuppets on 2007-02-11
I'm a newb running Kubuntu Edgy. I try to run Kate and I get this:

[COLOR="Blue"]
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
moshewe@moshewe-laptop:~$ kate
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QObject::connect: No such signal KListView::doubleclicked(QListViewItem*)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'KateSaveModifiedDialog')
[/COLOR]

Help?

---

### Post by aysiu on 2007-02-11
More info needed.

First of all, has this *always* happened ever since you installed Kubuntu, or is it recent?

Secondly, if it is recent, is it tied to an event? Something like you installed a new program or changing a setting? If so, what was the event?

Thirdly, do you just get the error and it goes to the next line in the terminal... or do you get the "error" and Kate opens just fine?

---

### Post by MasterOfMuppets on 2007-02-11
I get the error and then goes to the next line.
This has always happened.
I installed Ubuntu, because the Kubuntu LiveCD got stuck on the qtparted part, and then upgraded to Kubuntu.
Thing is, I still get the Gnome deskstop... but that's another problem, thought I should mention it anyways.
Kate has NEVER worked, regardless of what I install.

EDIT: got this the last time I tried it...

```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-6587' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_moshewe-laptop__0
and start dcopserver again.
---------------------------------

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
KCrash: Application 'kate' crashing...
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

drkonqi: cannot connect to X server :0.0

```

---

### Post by aysiu on 2007-02-11
I Googled a couple of your errors, and this seems closest:
[https://launchpad.net/ubuntu/+source/kdebase/+bug/64735](https://launchpad.net/ubuntu/+source/kdebase/+bug/64735)

Is it possible you're running the command ```
sudo kate
``` instead of ```
kate
``` or ```
kdesu kate
```?

---

### Post by MasterOfMuppets on 2007-02-11
I don't know what's the kdesu command, but I tried using kate to edit xorg.conf, which can only be done in sudo as much as I understand...

---

### Post by aysiu on 2007-02-11
> **MasterOfMuppets said:**
> I don't know what's the kdesu command, but I tried using kate to edit xorg.conf, which can only be done in sudo as much as I understand...
There's your problem. You shouldn't be using *sudo* with a graphical application, especially Kate.

The correct command is ```
kdesu kate /etc/X11/xorg.conf
``` More info here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by MasterOfMuppets on 2007-02-12
Thanks!
Gedit doesn't count as a graphical app? I managed to edit it with gedit...

---

### Post by aysiu on 2007-02-12
> **MasterOfMuppets said:**
> Thanks!
Gedit doesn't count as a graphical app? I managed to edit it with gedit...
You're supposed to use ```
gksudo gedit
``` and not ```
sudo gedit
``` but ```
sudo gedit
``` is not as harmful/defective as ```
sudo kate
``` is. Read the link.

---

### Post by MasterOfMuppets on 2007-02-12
I did kdesu kate to edit xorg.conf, and I got this:
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
Invalid entry (missing '=') at /tmp/kde-root/kconf_update1byCFb.tmp:1
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QObject::disconnect: Unexpected null parameter

```
It worked, I edited the file, changes were saved. Other than this log, there doesn't seem to be a problem :confused: The last line showed up when I closed kate.

---

### Post by g8m on 2007-02-12
Kate produces a lot of debug-information if not compiled with --disable-debug. The messages only show in terminal sessions and are mostly harmless.

---

