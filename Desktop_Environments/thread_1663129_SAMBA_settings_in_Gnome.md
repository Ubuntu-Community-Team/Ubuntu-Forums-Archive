---
title: "SAMBA settings in Gnome?"
date: 2011-01-09
forum: Desktop Environments
---

### Post by Tom Mann on 2011-01-09
Hi,

I've had a server running Gnome desktop (for laziness and easy setup) for around 3 months. I used Gnome to set up my SAMBA shares. Now I'm planning on making the server headless I've found that /etc/samba.conf doesn't contain the shares I previously set up. Does anyone know whether there is a separate .conf file for Gnome's SAMBA sharing and if so where I would find the file?

Thanks,
Tom

---

### Post by Morbius1 on 2011-01-09
If by Gnome you mean Nautilus the samba shares are defined here:
```
/var/lib/samba/usershares
```

---

### Post by Tom Mann on 2011-01-09
Thank you, just what I needed.

Tom

---

### Post by Morbius1 on 2011-01-09
You may or may not be interested in this but you can contunue to use "Nautilus-shares" even though you don't have Nautilus. That's because Samba calls it "Usershares" and it's built into Samba itself. Of course you can no longer use a GUI to create and delete shares but you can use the command line:

[http://ubuntuforums.org/showpost.php?p=10316901&postcount=2](http://ubuntuforums.org/showpost.php?p=10316901&postcount=2)

FYI

---

