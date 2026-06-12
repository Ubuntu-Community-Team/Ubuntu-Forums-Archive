---
title: "Pidgin Crashes when message received (begins conversation)"
date: 2009-06-20
forum: General Help
---

### Post by ottoshmidt on 2009-06-20
Binary package hint: pidgin

Pidgin 2.5.5
 Installed: 1:2.5.5-1ubuntu8.1

Ubuntu 9.04 - the Jaunty Jackalope
Kernel Linux 2.6.28-12-generic
Gnome 2.26.1

When receive message (no matter fomr Yahoo, or MSN) Pidgin terminates unexpectedly and immediately.
But if I start conversation first and leave chat window open everything works fine.


When try to get backtrace Pidgin freezes instead of Crashing... the last lines in gdb: "Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb48fbb90 (LWP 15814)]
0xb3da42d8 in ?? ()"

Last lines in pidgin -d before crash:

"(16:36:43) yahoo: 73 bytes to read, rxlen is 93
(16:36:43) yahoo: Yahoo Service: 0x4b Status: 1
(16:36:43) yahoo: 121 bytes to read, rxlen is 141
(16:36:43) yahoo: Yahoo Service: 0x06 Status: 1
(16:36:43) yahoo: yahoo_codes_to_html:  Returning string: 'hjgjhkl\'.
(16:36:44) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(16:36:44) dbus: The signal "blist-node-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
(16:36:44) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(16:36:44) dbus: The signal "conversation-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
(16:36:44) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(16:36:44) dbus: The signal "blist-node-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
(16:36:44) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(16:36:44) dbus: The signal "conversation-extended-menu" caused some dbus error. (If you are not a developer, please ignore this message.)
(16:36:44) prefs: /pidgin/conversations/toolbar/wide changed, scheduling save.
(16:36:44) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(16:36:44) dbus: The signal "conversation-displayed" caused some dbus error. (If you are not a developer, please ignore this message.)
(16:36:44) yahoo: 73 bytes to read, rxlen is 93
(16:36:44) yahoo: Yahoo Service: 0x4b Status: 1
(16:36:44) accels: saving accels to /home/ottoshmidt/.purple/accels
Segmentation fault"


did complete remove and install but the same...

---

### Post by Soul-Sing on 2009-06-20
I think it is the yahoo issue again...Please use the search option on the forum and take a look if your problems are similar to that of other users.
: [http://ubuntuforums.org/showthread.php?t=1191064](http://ubuntuforums.org/showthread.php?t=1191064)

---

### Post by ottoshmidt on 2009-06-20
oh, I disabled sound "Message received begins conversation" from preferences and it works now :)

---

