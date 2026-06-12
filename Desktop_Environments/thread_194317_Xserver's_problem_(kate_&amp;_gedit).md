---
title: "Xserver's problem? (kate &amp; gedit)"
date: 2006-06-11
forum: Desktop Environments
---

### Post by georgevn on 2006-06-11
I have some annoying problems with gedit and Kate on my Kubuntu 6.0.6
*Kate:
> 
qui@georgevn:~$ sudo kate /etc/X11/xorg.conf
Password:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
qstring_to_xtp result code -2
ScimInputContextPlugin()
Qt: Locales not supported on X server
QInputContext: no input method context available
QInputContext: no input method context available
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
QInputContext: no input method context available
QInputContext: no input method context available
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
qstring_to_xtp result code -2
QObject::disconnect: Unexpected null parameter
~ScimInputContextPlugin()


*Gedit:
> 
qui@georgevn:~$ sudo gedit /etc/X11/xorg.conf

(gedit:5888): Gdk-WARNING **: locale not supported by Xlib

(gedit:5888): Gdk-WARNING **: cannot set locale modifiers
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


Even though everything is still fine, or it looks like that, but I very much want to get rid of them. it sounds like some devices are not recognized but i don't know how to check what it is? can someone help me on this?

*1 more small thing: is the service x11-common necessary? should i turn on (at boot) or just leave it there?

---

### Post by georgevn on 2006-06-12
could someone please help me?

---

### Post by caserio on 2006-06-12
Hi,
In KDE use kate. In GNOME use gedit.

Next time press Alt-F2 then enter:
kdesu or gksu  /etc/X11/xorg.conf

You can safely ignore "X Error..." or edit your xorg.conf and comment all the lines concerning the wacom driver.

---

### Post by georgevn on 2006-06-12
I commented out all the lines related to wacom and the kde stopped booting at the kde bootplash blue screen, i think that way does not solve it.

---

### Post by K0LO on 2006-06-15
I have the same problem trying to run:

**kdesu kate <filename>**

I don't have gedit installed so I can't comment there.

This problem started with my distribution upgrade from Kubuntu 5.10 to Kubuntu 6.06

**kdesu konqueror** works fine but **kdesu kate** does not.

---

### Post by K0LO on 2006-06-16
This is really strange, but I managed to fix this problem as follows.

Press "ALT + F2" and type "kdesu kate" in the dialog box that opens. This opened Kate in a root session just like it is supposed to do.

After doing that ONCE, I can now type at a console "kdesu kate" and the command works normally. Go figure.

---

