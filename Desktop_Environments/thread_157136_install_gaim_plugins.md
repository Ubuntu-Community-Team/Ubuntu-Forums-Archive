---
title: "install gaim plugins?"
date: 2006-04-08
forum: Desktop Environments
---

### Post by amunimanghi on 2006-04-08
does anyone know how to install gaim plugins?

---

### Post by angkor on 2006-04-08
```
apt-cache search gaim
gaim-autoprofile - template-based profile generator for Gaim
gaim-encryption - gaim plugin that provides transparent encryption
gaim-extendedprefs - extended preferences plugin for the instant messenger gaim
gaim-guifications - toaster popups for gaim
gaim-hotkeys - Configurable global hotkeys for gaim
gaim-irchelper - IRC extensions for GAIM
gaim-meanwhile - gaim plugin for Meanwhile
gaim-otr - Off-the-Record Messaging plugin for gaim
gaim-themes - Smiley themes collection for gaim
gaim-thinklight - Blinks your ThinkPad's ThinkLight upon new messgaes
gaim-xmms-remote - gaim-plugin that lets you control XMMS from gaim

```

Note: I'm in dapper right now so I'm not sure all these plugins are available on Breezy

You can install these plugins from the repositories.

sudo apt-get install [the-plugin-you-want]

or use synaptic to install the package you want.

Others you can probably install by hand by downloading a .deb or the source.

---

### Post by amunimanghi on 2006-04-08
okay i got this:
> aim-extendedprefs - extended preferences plugin for the instant messenger gaim

How do i use it in gaim?

---

### Post by bionnaki on 2006-04-09
open the gaim preferences and enable it.

---

### Post by amunimanghi on 2006-04-11
okay they worked. i download a plugin back in a .tar.gz format. how would i install that?

---

