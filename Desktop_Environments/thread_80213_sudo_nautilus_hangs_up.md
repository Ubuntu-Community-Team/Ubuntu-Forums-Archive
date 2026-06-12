---
title: "sudo nautilus hangs up"
date: 2005-10-21
forum: Desktop Environments
---

### Post by aivars on 2005-10-21
Hello,
When i do in terminal sudo nautilus nothing happens and terminal window hungs up and i have to close the window.
What might be the problem?

Thanks a lot 
Aivars
Ubuntu 5.10

---

### Post by aysiu on 2005-10-22
Try ```
gksudo nautilus
```

---

### Post by aivars on 2005-10-22
Thanks for suggestion, now i get this after gksudo nautilus:

(nautilus:8810): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Thaks again

Aivars

---

### Post by graigsmith on 2005-10-22
it might be really bad to run nautilus with sudo.  for one, if nautilus saves any files in your home directory.  say hidden config files, it probably will save them with root's permissions.  Then your regular nautilus will stop working, because it wont be able to access the modifications root made.

---

### Post by aysiu on 2005-10-22
[QUOTE=aivars]Thanks for suggestion, now i get this after gksudo nautilus:

(nautilus:8810): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/QUOTE] Actually, you're supposed to run that command from the Run dialogue, but when I run it from the terminal, [I get that warning message, too--the only difference is that Nautilus actually opens up.](http://i22.photobucket.com/albums/b337/psychocats/1a7c18de.png)

---

