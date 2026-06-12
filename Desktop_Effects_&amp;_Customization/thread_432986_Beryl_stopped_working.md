---
title: "Beryl stopped working"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by Errorsol on 2007-05-04
Just like the title says, after I turned on my comp today beryl stopped working. It was working perfectly fine yesterday, now it just won't work at all.

Edit: nvm, fixed it.

---

### Post by Wakkarnc on 2007-05-04
How did you fix it? I am new to Ubuntu/linux, and I am generally really impressed, but today for no reason my audio stopped working, so I did a ctrl-alt-backspace... the audio was back, but now neither emerald nor beryl works. For some reason I only have two desktops when i press ctrl-alt-next and the beryl command to go to cubed-mode does nothing at all... I have checked the settings in the beryl-settings manager, and I can't see an obvious error in there. Any help will be appreciated. I run Nvidia Geforce and dual-screens, but this shouldn't really matter as it has worked untill now. 

When I write sudo-beryl in terminal it gives me this:
```
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
Checking maximum texture size                   : passed (4096x4096)

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
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!
****@****:~$ 

```

---

### Post by [Alsharifi] on 2007-05-10
same thing happened to me...if u dont mind can u tell me how u fixed it?

---

### Post by [Alsharifi] on 2007-05-10
bump..need help

---

### Post by Wakkarnc on 2007-05-23
Yeah, if you still need help, the solution I found was fairly obvious... Beryl automatically falls back to metacity when it crashes, just right-click on the beryl icon -> Select Window Manager -> Beryl... that did the trick for me at least.

---

