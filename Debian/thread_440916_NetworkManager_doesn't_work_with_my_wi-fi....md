---
title: "NetworkManager doesn't work with my wi-fi..."
date: 2007-05-12
forum: Debian
---

### Post by thully on 2007-05-12
In Debian, I can't seem to get NetworkManager  to work with my wi-fi (madwifi on MacBook).
If I click on one of the available access points to connect to it, it tries to connect forever - and never does.  If I use the GNOME Network control panel, I can connect. On Ubuntu, NetworkManager functions properly.  Does anyone have a clue about what is going on?

---

### Post by Pobega on 2007-05-13
I don't know about MadWiFi, but I use Intel's 3945 b/g wireless card.

I have to modprobe ipw3945, and make sure to run the regulatory daemon at boot. Maybe you'll wand to add an entry for madwifi to /etc/modules so that the module is loaded at boot time?

Again, I've never worked with MadWiFi, so if I'm wrong please correct me.

---

### Post by tturrisi on 2007-05-13
what version of debian?
Ubuntu uses a newer version of network-manager.
I prefer the Gnome net-admin anyway, it's simpler, always works and a no brainer.  network-manager is a buggy app.

---

### Post by shae on 2007-06-19
You should try compiling the new version of mad-wifi.

---

### Post by floke on 2007-06-19
gnome network manager - I HATE IT!!
Use wifi-radar and curse that craplet to the pits of hell :twisted:

---

