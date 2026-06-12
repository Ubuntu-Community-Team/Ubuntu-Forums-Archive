---
title: "kdeapp launch on gnome maxing out my cpu"
date: 2006-12-01
forum: Desktop Environments
---

### Post by amerikkanu on 2006-12-01
hey all,

my setup:  fresh install of edgy; scim + m17n; gnome desktop with kde installed for several apps.

not sure what the problem is.  got kvoctrain (vocabulary/flashcard program) up and running several hours ago.  it seemed to have problems with scim (which i'm using to input devanagari), but changing from one utf-8 font to another seemed to solve that problem.  then, without having run any updates, it now fails to launch and maxes out my cpu in an endless loop.  the error msg. i get, running it from the console is:

> 
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
Link points to "/tmp/ksocket-guy"
Link points to "/tmp/kde-guy"
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
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
Invalid entry (missing '=') at /tmp/kde-guy/kconf_updateCM9RFa.tmp:1


(The bad device errors I believe I was getting while it was still able to launch and run.)  Seems like a problem with the kde backend to my newbie eyes.  or maybe i have to go back and reconfigure scim for kde?  Can anybody decipher these errors?  Any suggestions?  All help much appreciated!

guy

---

### Post by amerikkanu on 2006-12-02
update: i've had a chance to try to troubleshoot this a bit and it seems not to be a kde problem per se, but a kde/scim problem.  every kde program i try (kvoctrain, kwordquiz, konqueror) crashes when i try to type the same characters in devanagari (non-initial vowels, "e" and "ai" when they would extend beyond the beginning of their preceding character).  so i'll close this thread and open a new one on scim, if i can't find the answers on my own.  thanks for looking.

---

