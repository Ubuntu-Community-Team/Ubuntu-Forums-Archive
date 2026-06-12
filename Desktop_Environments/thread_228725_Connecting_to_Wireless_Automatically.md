---
title: "Connecting to Wireless Automatically"
date: 2006-08-03
forum: Desktop Environments
---

### Post by breezyONE on 2006-08-03
This is probally an easy one, but I tried searching here and on google without luck. I was wondering how I could get the wireless to automatically connect to an AP when it is detected. Right now I have to go to wlassistant, put in the password, and then connect to the AP. If there is no way to do this, could someone provide me the shell command that could connect to an AP so I could write a perl script to do it when I login.

Thanks for the help!

---

### Post by paddy1978 on 2006-08-03
'Network manager' sounds like what you're after. In the repositories you'll find the KDE front-end - ['knetworkmanager']("http://packages.ubuntulinux.org/dapper/kde/knetworkmanager")- and the GNOME one - ['network-manager-gnome']("http://packages.ubuntulinux.org/dapper/net/network-manager-gnome"). 

They both sit in the tray and will automatically connect to wired/wireless networks (once you've entered passwords for the first time).

Hope this helps! :-)

---

