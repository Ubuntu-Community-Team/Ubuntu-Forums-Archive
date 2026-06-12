---
title: "Libgl_always_indirect"
date: 2009-01-06
forum: General Help
---

### Post by zika on 2009-01-06
ubuntu Intrepid
ATI Radeon HD 3650
latest driver from ati.amd.com with 8.12 Catalyst (10-dec-2008.)
compiz enabled

if I run fgl_glxgears in Terminal it just pops and go away (exits)

if I execute (in Terminal) ```
unset LIBGL_ALWAYS_INDIRECT
```fgl_glxgears runs ang gives me ~60.000 fps

also, before that command I get that I do not have direct rendering (because of that variable being set) and after that command I get that direct rendering is enabled (glxinfo).

once I exit the Terminal, the setting is gone.

I've checked /usr/bin/compiz and it uses glxinfo to determine if rendering should be direct.

is there any way I could make that setting (unset LIBGL_ALWAYS_INDIRECT) stick. I've tried making a Sessions entry, editing /etc/rc.local, ... but did not succeed.

yes, in metacity everything works.

what is also interesting is that if I call a terminal from the menu App->Acces.->Terminal rendering is direct. but if I call it by a shortcut (chosen by Preffered Applications) rendering is not direct ... plot thickens.

---

