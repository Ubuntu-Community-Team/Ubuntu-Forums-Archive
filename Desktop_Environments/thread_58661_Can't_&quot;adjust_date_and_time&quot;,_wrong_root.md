---
title: "Can't &quot;adjust date and time&quot;, wrong root passwd?"
date: 2005-08-21
forum: Desktop Environments
---

### Post by ree on 2005-08-21
[Kubuntu approx. 5 hours old on my laptop .... uber newbie]

Having just installed Kubuntu, I now need to change the clock - I recall seeing something about NPS failing when I boot (nice red asterisk), so assume something is out with my time settings.

Right-clicking on clock and choosing "Adjust Date and Time" brings up the "Run as root - kde su" dialogue box.  I enter in the root password - which I know is correct, because if I "su root" in terminal, it's correct - brings up an "incorrect password" message.  I'm assuming that I'm supposed to enter the root password, rather than my own (neither work)...?

Could someone point me in the right direction with this problem?

 ](*,)

---

### Post by jeremy on 2005-08-21
This is a known bug, the only way I can change this setting is to open a console, and do:
sudo kcontrol
This opens the control centre as root, then adjustments can be made under 'System Administration' -> 'Date & Time'.

---

### Post by ree on 2005-08-21
[QUOTE=jeremy]This is a known bug, the only way I can change this setting is to open a console, and do:
sudo kcontrol
This opens the control centre as root, then adjustments can be made under 'System Administration' -> 'Date & Time'.[/QUOTE]
Thanks for the suggestion, but sudo kcontrol gives me:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kcontrol: cannot connect to X server :0.0
ERROR: KUniqueApplication: Registering failed!
ERROR: Communication problem with kcontrol, it probably crashed.
```

---

### Post by hanasaki on 2007-07-17
I ran into the same thing on gnome and also with vlock under the root account... it seems to be tied to running under an account that does not have sudo permissions.

be careful... if you vlock -a on such an account you will need a remote login or reboot to get unlocked!

---

