---
title: "Setting the # of workspaces by configuration file?"
date: 2011-05-07
forum: Desktop Environments
---

### Post by triceratops on 2011-05-07
Hi,

  Recently upgraded two machines to 11.04 and xfce 4.8

   Which xfce configuration files control the number of workspaces on the desktop?  I've tried to use the gui settings manager to set the number of workspaces I prefer.  Sometimes xfce resets the number of workspaces to the the default four after I reboot.  Is there any way I can fix the number of workspaces from a shell configuration file?

    Oddly, this quirk only happens on one machine.  The laptop has more than enough memory to support a large number of workspaces.  Perhaps there's an underlying configuration issue that is causing the system to reset the number of workspaces?  Thanks

---

### Post by Toz on 2011-05-07
~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml

---

### Post by triceratops on 2011-05-07
great stuff, thanks

---

