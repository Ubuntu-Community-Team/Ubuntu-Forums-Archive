---
title: "Gnome Shell problems"
date: 2011-01-14
forum: Desktop Environments
---

### Post by elmodai on 2011-01-14
Dear all,

I have problems with Gnome Shell. Use Ubuntu dsktop 10:10.
 I installed the Gnome software store from Shell, after the isntallation compelete is, I tried to run with the "gnome-shell - replace" command on the terminal.

 The Following errors apear and the terminal the task never ends.

'JS ERROR: !!!   Unhandled type uint32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
    JS ERROR: !!!   Unhandled type int32 releasing GArgument
      JS LOG: GNOME Shell started at Fri Jan 14 2011 18:05:40 GMT+0200 (CAT)
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again
    JS ERROR: !!!   Exception was: TypeError: this._gdm.list_users is not a function
    JS ERROR: !!!     lineNumber = '70'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/statusMenu.js'
    JS ERROR: !!!     message = 'this._gdm.list_users is not a function'
    JS ERROR: !!!     stack = '([object _private_Gdm_UserManager])@/usr/share/gnome-shell/js/ui/statusMenu.js:70
([object _private_Gdm_UserManager])@/usr/share/gjs-1.0/lang.js:110
Error("Chained exception")@:0
("Chained exception")@gjs_throw:0
'
Window manager warning: Log level 8: meta_window_focus: assertion `!window->override_redirect' failed'

Alguem saber solucionar o problema?

Thanks

---

### Post by 3Miro on 2011-01-14
It is 

```
gnome-shell --replace
```

---

### Post by elmodai on 2011-01-15
> **3Miro said:**
> It is 

```
gnome-shell --replace
```
  Even so, the error persist...

---

