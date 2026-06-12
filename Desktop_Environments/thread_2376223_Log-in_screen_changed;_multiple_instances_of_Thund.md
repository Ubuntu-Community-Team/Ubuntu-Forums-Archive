---
title: "Log-in screen changed; multiple instances of Thunderbird and a Terminal"
date: 2017-10-31
forum: Desktop Environments
---

### Post by makem2 on 2017-10-31
I had a nice xubuntu installed alongside windows and I experimented (sadly)

I installed Kubuntu, Lubuntu and Xfce desktops to decide if I preferred any one to the default xubuntu desktop. I installed Lubuntu first using Ubuntu Software Centre and realised it should have been Kubuntu. Without exiting the software centre, I uninstalled Lubuntu and installed Kubuntu. I rebooted and was faced with a different log-in screen This one was black and had the Ubuntu icon which allowed selection of other desktops. (LXDE; OPENBOX; Plasma; Xfce; xubuntu)

To cut a long story short, in my efforts to get back to the xubuntu default log-in screen I lost all desktops and was unable to log in. Using a live usb I recovered the system and installed xubuntu desktop via the live usb. The system is working except for some start up after log-in problems and I still have the black log-in screen.

The start up problems are:

1. An instance of terminal pops up

 2. Multiple instances of Thunderbird (4)

3. Thunderbird account errors asking me to wait until processing is complete. One for each client instance

Please advise if it is possible to edit the script (presumably a script?) which boots the desktop to prevent these spurious multiple instances which may stem from multiple previous desktops.

EDIT: Session & Startup Autostart shows the Xfce Settings Daemon and KDE Connect daemon running

The Session shows xfce4- panel, Xfsettingsd and xfdesktop are running

Compatibility, launch GNOME services on startup

---

### Post by makem2 on 2017-10-31
It looks like it may be solved except for the black login screen with the multi choices ubuntu icon.

I closed Thunderbird down, closed Terminal down, renamed the .cache and rebooted.

Only one instance of Thunderbird arrived and no Terminal.

Unless someone come with a solution of how to get back to the default xubuntu login screen, I will live with the black screen. No more experimenting on my running system Perhaps I will use live usb's to see which I prefer - if that is possible.

---

