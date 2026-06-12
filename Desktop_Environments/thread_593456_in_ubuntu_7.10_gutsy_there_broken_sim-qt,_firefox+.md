---
title: "in ubuntu 7.10 gutsy there broken: sim-qt, firefox+flash, poweroff applet"
date: 2007-10-27
forum: Desktop Environments
---

### Post by qmax on 2007-10-27
Just upgraded to ubunty 7.10 gutsy and expirience broken behaviours:

[LIST=1]
[*]sim and sim-qt just segfaults upon opening chat window OR when started w/out ~/.sim
[*]firefox segfaults when opening flash (nspluginwrapper)
[*]poweroff button / session end applet hangs for a 1-1.5 minutes before drawing its window
[/LIST]

arch: amd64

---

### Post by qmax on 2007-10-27
after reinstalling nspluginwrapper and mozilla-flash-plugin,
firefox stoped segfaulting, but now draws only square in place of swf object and spits in console:

*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_NewStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed

---

