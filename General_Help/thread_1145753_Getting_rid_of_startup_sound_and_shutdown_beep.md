---
title: "Getting rid of startup sound and shutdown beep?"
date: 2009-05-01
forum: General Help
---

### Post by liquidcross on 2009-05-01
I've got sound alerts on my laptop (a Thinkpad R60, running 9.04) turned off, but I still get the login screen sound, and when I shutdown, I get a system beep. Is there any way to disable both of those?

---

### Post by Yellow Pasque on 2009-05-02
For the GNOME login jingle:
System -> Preferences -> Startup Applications

I don't know about the shutdown sound. Maybe look into blacklisting pcspkr and/or snd_pcsp modules.

---

