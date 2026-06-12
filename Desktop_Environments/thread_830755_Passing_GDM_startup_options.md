---
title: "Passing GDM startup options"
date: 2008-06-16
forum: Desktop Environments
---

### Post by randysparks on 2008-06-16
I need to pass GDM some startup options. 

Does anybody know what's responsible for starting GDM on Hardy?

---

### Post by NikoC on 2008-06-16
I'm not sure about this one, but I think all that is launched during bootup is copied in:
/etc/init.d

(gdm is in there as well, so it boots at startup).

Wait for confirmation from another member though ;)

edit: Just tried it out:
sudo mv /etc/init.d/gdm ~/Desktop
And when I rebooted it left me a login 'prompt'
To restore my Gnome boot:
sudo mv ~/Desktop/gdm /etc/init.d/

---

