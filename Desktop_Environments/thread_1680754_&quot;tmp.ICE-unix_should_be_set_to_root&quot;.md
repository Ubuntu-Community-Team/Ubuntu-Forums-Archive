---
title: "&quot;/tmp/.ICE-unix should be set to root&quot; ??"
date: 2011-02-03
forum: Desktop Environments
---

### Post by watchpocket on 2011-02-03
[COLOR=DarkRed]***Problem***[/COLOR]: Line 4 of my ~/.xsession-errors file says:

 ```
_IceTransmkdir: Owner of /tmp/.ICE-unix should be set to root
```Owner and group for that file, I notice, is "gdm".

( and, in case they're relevant, here are the first three lines of ~/.xsession-errors:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/rj/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/none. )

[COLOR=DarkRed]***Solution***[/COLOR]: run this command:```
sudo chown root:root /tmp/.ICE-unix
```; rename ".xsession-errors" to ".xsession-errors.old" and reboot.

Except it's not a solution, because line 4 of the newly regenerated .xsession-errors file still says:

"_IceTransmkdir: Owner of /tmp/.ICE-unix should be set to root"
 
*Should* /tmp/.ICE-unix in fact be set to root?  If so, why does it get set back to "gdm" on re-boot?  And what should I do about it?

---

