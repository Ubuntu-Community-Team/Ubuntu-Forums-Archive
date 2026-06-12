---
title: "ratpoison not appearing in sessions list"
date: 2007-01-16
forum: Desktop Environments
---

### Post by crashboom on 2007-01-16
Hello all--

Used to linux but new to ubuntu and loving it.

I'm having trouble getting directly to the ratpoison window manager directly from the login screen. I installed both it and fluxbox (using aptitude); fluxbox showed up in the "Select Sessions..." box but ratpoison didn't.

I can get to ratpoison indirectly by going first into fluxbox and then by selecting ratpoison as a window manager. But it would be nice to be able to go direct.


Thanks,

Erick

---

### Post by unless on 2007-04-13
Sorry for the lag in replying to you... I rarely stop into the forums. 'Hope you're still using Ubuntu! If you still haven't found the answer to your problem...

If you're using gdm to handle logging in, then this should work:

Create the file /usr/share/xsessions/ratpoison.desktop with the following contents:

```

[Desktop Entry]
Encoding=UTF-8
Name=Ratpoison
Comment=Start Ratpoison as your window manager
Exec=ratpoison
Icon=
Type=Application

```

Cheers.

---

