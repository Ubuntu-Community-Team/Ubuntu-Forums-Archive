---
title: "Desktop icons in GNOME 3.28 - still need them"
date: 2019-08-22
forum: Desktop Environments
---

### Post by setonic on 2019-08-22
I still want to have desktop icons in my GNOME 3.28. I believe someone aready has a solution how to get them BACK. Please, share with us your solution.

---

### Post by #&amp;thj^% on 2019-08-22
They are gone, it&#8217;s by design. But you can try to reenable them with:
```

gsettings set org.gnome.desktop.background show-desktop-icons true
```

and starting/re-starting nautilus 
And if you need the # show shares on desktop
```

gsettings set org.gnome.nautilus.desktop volumes-visible true
```
```

# restart nautilus
nautilus -q
nautilus
```

EDIT: Earlier this year, the GNOME devs decided to remove the ability of the Nautilus (Files) file manager to handle desktop icons, stating with the GNOME 3.28 release, promising to bring it back as soon as possible through a new implementation in the form of a GNOME Shell extension.
> GNOME developer Carlos Soriano announced today that the forthcoming GNOME 3.30 desktop environment is bringing back the beloved GNOME Classic mode that allows users to use desktop icons.

---

### Post by deadflowr on 2019-08-22
The above should work.
You can also do the same through gnome tweaks (also known as Tweaks in the Software store)
Should be a setting in the Desktop section of tweaks.

Ubuntu that ships with gnome 3.28 ships the older 3.26 version of nautilus.

---

### Post by setonic on 2019-08-22
Thanks for replies. Commands did not work, but tweak made desktop icons appear. Still some issue with drug and drop TO the desktop, but not from desktop.

---

