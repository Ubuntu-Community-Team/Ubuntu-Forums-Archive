---
title: "Flash freeze error messages (firefox)"
date: 2009-02-06
forum: General Help
---

### Post by Mzwo on 2009-02-06
hi,

when running firefox via terminal i get the following messages:


```
mzwo@Mzwo:~$ firefox
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/plugins/libflashplayer.so [/usr/lib/firefox-addons/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x621da0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
GCJ PLUGIN: thread 0x621da0: NP_GetValue
GCJ PLUGIN: thread 0x621da0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x621da0: NP_GetValue return
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()

```

all this before opening any page. when loading youtube or similar, firefox freezes for a bit. output then is as follows:

```

(npviewer.bin:8123): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:8123): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
*** NSPlugin Wrapper *** ERROR: NPClass::HasProperty() wait for reply: Message timeout
*** NSPlugin Wrapper *** ERROR: NPClass::HasMethod() wait for reply: Message type invalid
*** NSPlugin Viewer  *** ERROR: NPN_Evaluate() wait for reply: Message type invalid
*** NSPlugin Viewer  *** ERROR: NPN_ReleaseObject() invoke: Message type invalid
*** NSPlugin Viewer  *** ERROR: NPN_GetValue() invoke: Message type invalid
*** NSPlugin Viewer  *** WARNING: unhandled variable 15 in NPN_GetValue()
*** NSPlugin Wrapper *** ERROR: NPClass::Invoke() invoke: Message type invalid
*** NSPlugin Viewer  *** ERROR: NPN_GetURLNotify() invoke: Message type invalid
```


i have no idea what all this means, but it doesn't look right. what to do?
i'm using flash 10.


thanks,
Mzwo

---

### Post by markharding557 on 2009-02-06
try uninstalling flash and reinstalling,make sure it is the one in ubuntu repo

---

### Post by Mzwo on 2009-02-06
did that already. same problems with flash 9 (which is what i get from the repos). that aside, flashplugin-nonfree currently fails to install flash, i get 404-errors.

Mzwo

---

### Post by Mzwo on 2009-02-09
bump

---

### Post by Mzwo on 2009-02-10
bump

---

### Post by Mzwo on 2009-02-19
bump.
anyone?

---

### Post by Mzwo on 2009-02-22
bump!

---

### Post by Mzwo on 2009-02-25
.... bump ....

---

### Post by jrela2000 on 2009-02-25
i have been researching for 5 hours and I really believe that there is not a fix for this issue yet.


 no one will just say that, though...

---

### Post by Mzwo on 2009-02-25
ok, thanks. i'll sit tight, then :-k.

Mzwo

---

