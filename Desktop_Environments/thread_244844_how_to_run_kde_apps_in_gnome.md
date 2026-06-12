---
title: "how to run kde apps in gnome?"
date: 2006-08-27
forum: Desktop Environments
---

### Post by ravikm on 2006-08-27
hi,

i have installed octave & koctave.

octave works fine, but koctave when run from command line says:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-ravi"
Link points to "/tmp/kde-ravi"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kOctaveui.rc
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Launched ok, pid = 5956
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
No lib found, check that kdebase is properly installed!
KCrash: Application 'koctave' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
ravi@ravi-ubuntu:~$ ICE default IO error handler doing an exit(), pid = 5953, errno = 0

when i run koctave from applications menu, says:

Octave path is not set, but found what seems to be Octave
Will try to use /usr/bin/octave

do i have to install Kubuntu? or is there any work around?

---

### Post by majestros on 2007-04-24
installing kdebase with synaptic solved my problem, koctave works fine now.  

After I noticed you posting their error messages from the terminal, I ran it from the terminal and my errors specifically mentioned "do you have kdebase installed correctly?"

After installing kdebase and its associated packages, it works fine.

My desktop still looks the same, but I don't know what will happen when I restart ;)

---

