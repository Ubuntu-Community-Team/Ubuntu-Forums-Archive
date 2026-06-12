---
title: "deep problems"
date: 2005-08-16
forum: Desktop Environments
---

### Post by tmasboa on 2005-08-16
OK i'm on the edge of my nerve. I just had to retype this
because i hit the wrong key in Lynx. 
OK, I changed the Driver line in /etc/X11/xorg.conf from
"ati" to "vesa". When i restarted the x gave me error,
switched the runlevel to 2, and gave me console.
Before i rebooted I edited /tec/X11/xorg.conf as stated 
above, and also installed 3ddesktop and Ksensors.
I uninstalled Ksensors after it ruined Firefox and now
Firefox when you open it(now i can't because the x wont
start up), it has a jumbled GUI and isn't usable.
Right now, i'm in lynx and i can't get the x to start. 

Could someone please help?

Thank you,

Tmasboa
edit: i forgot to add, I put the "vesa" back to "ati" but it
didn't help

---

### Post by tmasboa on 2005-08-16
[QUOTE=tmasboa]OK i'm on the edge of my nerve. I just had to retype this
because i hit the wrong key in Lynx. 
OK, I changed the Driver line in /etc/X11/xorg.conf from
"ati" to "vesa". When i restarted the x gave me error,
switched the runlevel to 2, and gave me console.
Before i rebooted I edited /tec/X11/xorg.conf as stated 
above, and also installed 3ddesktop and Ksensors.
I uninstalled Ksensors after it ruined Firefox and now
Firefox when you open it(now i can't because the x wont
start up), it has a jumbled GUI and isn't usable.
Right now, i'm in lynx and i can't get the x to start. 

Could someone please help?

Thank you,

Tmasboa
edit: i forgot to add, I put the "vesa" back to "ati" but it
didn't help[/QUOTE]
 is anyone going to help?

---

### Post by Juergen on 2005-08-16
> is anyone going to help?
Well, 20min isn' t much time, even if it is somehow urgent to you.

Can you switch to another term (e.g. via <ALT><F2>), do a 'startx' and somehow copy the (error-)messages to a posting here?

Without exact messages the people here probably can't help much...

---

### Post by tmasboa on 2005-08-16
[QUOTE=Juergen]Well, 20min isn' t much time, even if it is somehow urgent to you.

Can you switch to another term (e.g. via <ALT><F2>), do a 'startx' and somehow copy the (error-)messages to a posting here?

Without exact messages the people here probably can't help much...[/QUOTE]
 actuall the problem is that it says that it can't find the "keyboard" module and driver 
i don't think i can copy the errors because i don't think i could get them into lynx. right now i'm in windows.
and somehow, it is a little urgent to me. i like a working computer.

---

### Post by az on 2005-08-16
I love lynx!

Type 

init 1

, or boot into recovery mode.

at the command line run
dpkg-reconfigure xserver-xorg
and take the default for everyting.  (That includes autodetection)

then run 
init 2
and "your welcome."

---

