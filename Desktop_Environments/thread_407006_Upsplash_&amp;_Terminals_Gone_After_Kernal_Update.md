---
title: "Upsplash &amp; Terminals Gone After Kernal Update"
date: 2007-04-11
forum: Desktop Environments
---

### Post by awells527 on 2007-04-11
My computer ran some updates that came out today, and when I rebooted, the splash screen was gone.  The screen just says "Starting up..." until it goes to the login screen.  I guess that's not the biggest deal, but my terminals (CTRL+ALT+F1, CTRL+ALT+F2, ETC) are gone as well, and I need those.

I'm guessing it could be something in my grub file since I saw it updated that after installing the updates.  Any help would be appreciated.

---

### Post by Madmoose on 2007-04-11
My splash screen also is messed up since the update. Did it to both my laptop, and the desk top.

This is the splash screen I use: [COLOR="DarkGreen"][Long URL click here!]("http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468")[/COLOR]

Thanks, 

Moose.

---

### Post by awells527 on 2007-04-12
I found the answer...

```
sudo update-initramfs -u
```

I found it in the tutorial for that Fingerprint theme you linked to.

---

