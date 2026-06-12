---
title: "beryl problem"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by speedisso on 2007-05-28
hi 2 all i just installed beryl on my ubuntu 7.04 but it gave me his error, maybe can someone help me
```

root@laptop:/home/speedisso# beryl-manager 
root@laptop:/home/speedisso# ************************************************************** 
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

beryl: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed 
Reloading options 
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. 
beryl: Plugin 'dbus':initDisplay failed 
beryl: Couldn't activate plugin 'dbus' 
Couldn't initialise dbus. This should not happen! 
```

---

### Post by speedisso on 2007-05-30
no one ??? please i really need help because the compiz doesn´t work either...my card is a nvidia 6200 turbocache se

---

### Post by infurnus on 2007-06-01
im having very similar problems i either uninstall beryl or use metacity to circumvent the problem though i would post output of my error, as well looking for some sort of resolution. I've notice this to be a problem with may other users too, and beryl always launches but as soon as i close terminal or escape it takes all of the menu bars and sticks my windows so i have to use alt click to move them :-(

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

beryl: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Reloading options
beryl: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
beryl: Plugin 'dbus':initDisplay failed
beryl: Couldn't activate plugin 'dbus'
Couldn't initialise dbus. This should not happen!

```

---

