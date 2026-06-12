---
title: "'Switch User' problem"
date: 2007-09-28
forum: Desktop Environments
---

### Post by witch_doctor on 2007-09-28
This issue is not specific to ubuntu, as it occurs on other distos I have used too  (Debian 3, Fedora 7) 
   
This only happens when using a CRT screen. I've checked xorg.conf and I 've used 3 different CRT screens, to make sure it is not a misconfiguration or hardware problem.

I use Gnome as my desktop manager. It happens when someone loged in from the 'Switch user' menu button on the locked screen window of another user, logs out. 
 It doesn't always happen. I estimate 1 out of 3 times. Exactly the same problem occurs when pressing ctrl-alt-Fkey to switch to another virtual console, and then switch back to F7 on which the X server runs.

  The screen freezes and there is no login prompt. Killing the X server by ctrl-alt-backspace blanks the screen for a second or two, and then the same frozen screen appears. 
  If left for a while, the system freezes completely, and there is no response to the keyboard. Only a hard reset can make the machine recover.   
  The only way to recover without rebooting is to log in to a console by alt-ctrl-Fkey shortly after the problem starts, switch to runlevel 1 and then back to runlevel 3.

---

### Post by bluenova on 2007-09-28
Happens with KDE too.

---

### Post by Kev0r on 2007-09-29
This happens with me too, switch user -> freeze...

no way to recover except for a hard reset.

Acer Espire 5100, with an Ati inside.

---

### Post by louieb on 2007-09-29
Does it on mt IBM T30 laptop. But my desktop hasn't froze yet. Did not have the problem when using Dapper. It started for me when I  installed Feisty. Theres a confirmed but report on fast user switching.   [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")

---

