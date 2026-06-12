---
title: "Beryl just broke"
date: 2007-02-20
forum: Desktop Environments
---

### Post by tbeld on 2007-02-20
Hi all,
I've been using Beryl SVN for a while now with minimal issues but I just did an update and now I get complete whiteness after log in. I can rotate my cube- whiteness on all 4 sides and my caps are normal but nothing else is there- just a vast whiteness. I'm guessing others are having this issue?

---

### Post by kelbizzle on 2007-02-20
you may want to check over at beryl-project.org. As their scope mainly pertains to the support of beryl. Also...If an update bugged out on you. I'm sure they'd like to hear about it.

---

### Post by tbeld on 2007-02-20
> **kelbizzle said:**
> you may want to check over at beryl-project.org. As their scope mainly pertains to the support of beryl. Also...If an update bugged out on you. I'm sure they'd like to hear about it.

Good point... Done.

---

### Post by chalewa on 2007-02-20
just wait till tomorrow all will be fine i am sure

---

### Post by tbeld on 2007-02-27
Well, all isn't fine. I ran some more updates and still no magic. I no longer have the "whiteness" I was referring to but I also crash and fall back to plain-jane Gnome:mad:

---

### Post by tbeld on 2007-03-12
I found a solution that works for me. It was to go Beryl Manager -> Advanced Beryl Options -> Rendering Path and select Copy.

l have an ATI.

---

### Post by cleatus on 2007-03-12
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2046x2046)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2046x2046)

Reloading options
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!


Just started getting this what is happening....also gettin g random lockups.

---

