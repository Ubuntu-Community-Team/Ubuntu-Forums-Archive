---
title: "How to Disable Desktop Effects from Starting?"
date: 2008-06-03
forum: Desktop Environments
---

### Post by davinci0212 on 2008-06-03
I downloaded some Ubuntu security updates yesterday and when I rebooted, I was unable to successfully log into Gnome. I got through the login screen, but when logging in, all I can see is this whitish background; no desktop, no menus, etc. I can still activate Expose, but all I can see is a zoomed out whitish background. I am able to get into a Gnome failsafe session. 

I have a Thinkpad T43p with ATI graphics. I believe these are relevant error messages from dmesg:

[  144.104996] fglrx: disagrees about version of symbol struct_module
[  590.385308] compiz.real[6792]: segfault at 04790436 eip 08055a80 esp bff864e0 error 4
[  222.420181] fglrx: disagrees about version of symbol struct_module

I think I can log in to a normal Gnome session if I can disable Compiz from running. Is there a way I can turn this off in a text file? 

Many thanks from a N00b!

---

### Post by spadewarrior on 2008-06-03
Try Alt+F2 then in the box type

```
metacity --replace
```

If that works, add it to your startup in the prefs/admin area (can't remember where that is on GNOME, not used it in a while).

Hope that helps. :)

---

### Post by davinci0212 on 2008-06-03
Thanks spadewarrior. The funny thing is that I was prompted to install more security updates during the Gnome failsafe session. When I restarted all became good with Gnome. Compiz is now working fine. 

....go figure, right? :)

> **spadewarrior said:**
> Try Alt+F2 then in the box type

```
metacity --replace
```

If that works, add it to your startup in the prefs/admin area (can't remember where that is on GNOME, not used it in a while).

Hope that helps. :)

---

### Post by spadewarrior on 2008-06-03
Very strange. No idea about that! I'm a noob too. Glad you're sorted now.

:)

---

