---
title: "Remove a shortcut from Dash"
date: 2011-08-21
forum: Desktop Environments
---

### Post by pgn674 on 2011-08-21
I have Ubuntu 11.04, upgraded from 10.10, and I'm logging into the default Ubuntu, Unity. In Dash, if I search for "firefox", I get three results:
Firefox Web Browser
Mozilla Firefox
Mozilla Firefox (Safe Mode)

Clicking Firefox Web Browser brings up Firefox just fine. But both Mozilla Firefoxes do nothing. I have a feeling that they're left over from Wine, but I'm not sure. The Uninstall Wine Software program doesn't show Firefox, but I may have uninstalled it through there a long time ago.

I want to remove these shortcuts from Dash. I tried checking the Main Menu program, but Mozilla Firefox isn't in there (though Firefox Web Browser is). I looked in /usr/share/menu/, and found a file called "firefox". That file specifies a title of "Firefox Browser", so I'm not sure if it even applies. The command it gives, "/usr/bin/firefox", is good, anyway. I don't see any other firefox related file there.

So, does anyone know how I remove those shortcuts from Dash?

---

### Post by kerry_s on 2011-08-21
~/.local/share/applications

that's a hidden folder by the way, open the file manager & press ctrl+h to see hidden.

---

### Post by isa.dsouza on 2012-10-31
This helped to delete the shortcut for a website that was created by Midori. Thanks.

---

