---
title: "[SOLVED] No CD no DVD"
date: 2008-12-12
forum: General Help
---

### Post by osurshaney on 2008-12-12
I have been having a problem with my CD and DVD drives.  First they were back wards in my computer properties.  So....I shut the computer down and switched them.  Now neither is recognized.   I can't even put in the install disk and go from there.  I keep getting SRST Failed (errno=16) and failed to get xfermode when I reboot.  There is power to them and I tried switching them back.  I don't know what the hell happened.  Very inconvenient either way.  Is there a way to check for hardware or something similar?  Reboot takes forever and I don't know what happened.  Please help.  I cant even reformat and start over...

---

### Post by Gausian on 2008-12-12
do you have your master/slave configuration right?  try only one at a time and see if that helps.

---

### Post by theozzlives on 2008-12-12
Try using your best drive set to "Master".

---

### Post by osurshaney on 2008-12-12
I switched the master/slave configuration.  They are recognized now but they are reversed again.  Strange.  When I insert a audio cd I can open it with my media player.  But dvd's nothing.

---

### Post by Gausian on 2008-12-12
is it a movie or softwate/data dvd?  have you tried different dvd's all with the same result?

---

### Post by mc4man on 2008-12-12
Run and post these, possibly a very simple fix.

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```
```

sudo lshw -C disk
```

---

