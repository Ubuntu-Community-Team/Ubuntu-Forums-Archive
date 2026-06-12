---
title: "Login Screen (GDM) Resolution"
date: 2006-01-02
forum: General Help
---

### Post by j-a-p on 2006-01-02
I have my desktop resolution set at 1280x1024 but the login screen (GDM) displays using a resolution 1920x1440 which is too high for me.  How can I set this to the same as the desktop resolution?

Thanks

---

### Post by felipefoz on 2006-01-02
[QUOTE=j-a-p]I have my desktop resolution set at 1280x1024 but the login screen (GDM) displays using a resolution 1920x1440 which is too high for me.  How can I set this to the same as the desktop resolution?

Thanks[/QUOTE]

I solved this reconfiguring de x.server with the command 

$sudo dpkg-reconfigure xserver-xorg

and taking off the high resolutions which i couldn't use, or
you can manually edit the xorg.conf and taking these resolutions off (dangerous options), hehehe

---

### Post by j-a-p on 2006-01-02
That worked great.  I looked at the /etc/X11/xorg.conf file after and all it did was remove the entries for the unwanted resolutions.

Thanks felipefoz.

---

