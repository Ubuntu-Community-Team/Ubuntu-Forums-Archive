---
title: "Reduce size of KMenu icons"
date: 2005-10-19
forum: Desktop Environments
---

### Post by goldenboy on 2005-10-19
Ok, I changed from hoary to breezy yesterday and besides other annoying changes, that I've not spent much attention on till now, the increased size of the Icons in the KMenu makes me hate my beloved KDE Desktop.

It seems that the default icon size for each kicker menu changed from 16x16 to 22x22. I hope this is an option so I can again change it to 16x16, but how is this possible - if it is?

cheers

---

### Post by GeneralZod on 2005-10-19
This might help:

[http://wiki.kde.org/tiki-index.php?page=Kicker+Hacks](http://wiki.kde.org/tiki-index.php?page=Kicker+Hacks)

---

### Post by goldenboy on 2005-10-19
[QUOTE=GeneralZod]This might help:

[http://wiki.kde.org/tiki-index.php?page=Kicker+Hacks](http://wiki.kde.org/tiki-index.php?page=Kicker+Hacks)[/QUOTE]


Yes it helped :)

Had to adjust the settings in /usr/share/kubuntu-default-settings/kde-profile/default/share/config/kickerrc

Thanks

---

### Post by goldenboy on 2005-10-25
Ok doing the changes in /usr/share/kubuntu-default-settings was no good idea since after each update the changes are gone.

But adding the appropriate options to the ~/.kde/share/config/kickerrc of course makes the changes persist.

P.S.: the konqiconviewrc configuration file i also interesting since one can set the default icon size back to 32 not keeping the idiotic 64 - not meaning to offense anyone, but who wants the icons to be that large by default??

---

### Post by travis_pl on 2007-05-11
The easiest way to change Kmenu icons size is to execute the following command:

```
kwriteconfig --file kickerrc --group menus --key MenuEntryHeight 16
```

The final result is the same as in manual editing of ~/.kde/share/config/kickerrc

Cheers.

---

