---
title: "Is printing configuration broken in Xubuntu Dapper?"
date: 2007-01-20
forum: Desktop Environments
---

### Post by Kadin2048 on 2007-01-20
I have Xubuntu Dapper (6.06LTS) up and running beautifully on an old Compaq (600MHz Celeron, ~300MB RAM).

However, I've been having an absolute devil of a time getting USB printing working. I'm starting to suspect that printing is somewhat broken in Xubuntu's default configuration.

Cups is installed and apparently working okay, but there doesn't seem to be any GUI configuration tools available for it. And when you go to CUPS' web interface (at [http://localhost:631](http://localhost:631) ), there is a messate saying that "Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing)."

Unfortunately, that GUI tool doesn't seem to exist in Xubuntu, or at least doesn't come up in the menu.

This seems like a problem/bug, unless I'm missing something. Can anyone confirm this, and what the preferred workaround is? I'd prefer not to install any software that I don't have to on this system, so I'm wary of installing the GNOME tool, particularly if it's going to have a lot of dependencies and require a lot of libraries and GNOME stuff to get installed.

I'm sure there are ways to configure CUPS from the CLI, but it's just obnoxious that it seems to not work 'out of the box.' Is this a known issue?

---

### Post by Mike_Longbow on 2007-01-20
In Xubuntu, there should be some programs called "xfprint4" and "xfprint4-manager", they work along with cups... Tought I have never tried them myself...
On the other side, I've found a document inside the xfce help wich explains some about this, it should be located in:
/usr/share/xubuntu-docs/desktopguide/C/printer-configuration.html
(copy the location in firefox)

---

### Post by Kadin2048 on 2007-01-20
Interesting. What I decided to do for the short term, was add the cupssys (?) user to the shadow group, so that it can read the shadow password file. This seems to make the web administration interface accept my normal username and password and add a printer (which worked fine).

However, I'm not sure if this is a security risk. I can't decide how it would be, but that's not really my area, so I try to be cautious.

Odd that the xfprint4 and xfprint4-manager programs aren't in the menu system. I had no idea they existed.

---

### Post by kerry_s on 2007-01-20
In dapper i just went with the gnome-cups-manager.

---

### Post by Kadin2048 on 2007-02-09
> **kerry_s said:**
> In dapper i just went with the gnome-cups-manager.

I thought about doing this, but I REALLY didn't want to have to install all the Gnome libraries, since I'm running on a system with very limited resources. I'm trying to stick with vanilla GTK+ apps, no Gnome stuff. So far I seem to be doing okay.

---

