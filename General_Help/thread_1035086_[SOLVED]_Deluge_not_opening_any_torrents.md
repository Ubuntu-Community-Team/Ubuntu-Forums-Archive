---
title: "[SOLVED] Deluge not opening any torrents"
date: 2009-01-09
forum: General Help
---

### Post by cyclone5uk on 2009-01-09
Strange behaviour in Deluge (latest version) on Ubuntu 8.10: 

Following a recent system update to Ubuntu, Deluge no longer lists any torrents. All the files I had been downloading before the update have vanished from the Deluge window and I am unable to add any new torrent files. 

Even when I save the tracker file to my home folder, then locate and try to open it using Deluge nothing appears in the Deluge main window.

---

### Post by cyclone5uk on 2009-01-12
Still not working.

C'mon guys, don't make me boot back into Windows!

---

### Post by blazemore on 2009-01-12
You could try uninstalling and reinstalling deluge
```
sudo apt-get remove deluge* -y && sudo apt-get install deluge* -y
```

---

### Post by adamlau on 2009-01-12
What blazemore said. Else, try Transmission. I recommend you give aria2 a shot once you get used to Ubuntu and familiarize yourself with the CLI :) .

---

### Post by ushimitsudoki on 2009-01-12
This happens from time to time to me as well.

Usually if I make sure all the deluged and python threads are killed, and then restart deluge, things come back to normal.

Deluge is good - but still a bit buggy.

---

### Post by blazemore on 2009-01-12
I actually quite like running uTorrent through Wine.
I found a guide to Wine desktop integration, where it had a comparison of colours: what Wine calls them, and what Gnome/KDE calls them. If anyone could find this guide, it's really useful so plz post it here!

---

### Post by cyclone5uk on 2009-01-12
I did give Transmission a try, but didn't like the interface. I really like Deluge, so would prefer to stick with it.

blazemore - I'll give the uninstall/reinstall a try when I get home this evening.

Thanks

---

### Post by cyclone5uk on 2009-01-12
> **blazemore said:**
> You could try uninstalling and reinstalling deluge
```
sudo apt-get remove deluge* -y && sudo apt-get install deluge* -y
```

That seems to have worked. Thanks!

---

