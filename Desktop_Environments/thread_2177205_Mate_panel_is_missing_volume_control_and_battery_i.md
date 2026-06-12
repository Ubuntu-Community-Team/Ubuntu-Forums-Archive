---
title: "Mate panel is missing volume control and battery indicator"
date: 2013-09-27
forum: Desktop Environments
---

### Post by suomalainen on 2013-09-27
Ubunteros,

I just installed MATE 1.6.0 on top of 12.04 and the volume and battery indicator are missing from panel. I did the right click on panel to add but they aren't lister there or in notification area.

What can I do next?

Thanks

---

### Post by suomalainen on 2013-09-27
I found these instructions:

Nu installeren we de MATE desktop manager, hier draait het uiteindelijk om. We installeren zo min mogelijk extra addons. Daarnaast installeren we caja open terminal voor de file manager, tekst bewerker en Firefox als de web browser wat handig kan zijn om je lokale scripts te testen.

    $ sudo apt-get update
    $ sudo apt-get install mate-archive-keyring mate-core mate-indicator-applet indicator-applet mate-notification-daemon mate-text-editor caja-open-terminal xinit firefox

Which restored the volume control but battery indicator is still missing.

Any thoughts?

---

### Post by suomalainen on 2013-09-29
I found some packages in mate not installed and installed them and now problems are gone. I used Synaptic package to find them.

---

### Post by suomalainen on 2013-09-29
I found some packages in mate not installed and installed them and now problems are gone. I used Synaptic package to find them.

---

