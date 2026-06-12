---
title: "SMB4K Configuration Problem"
date: 2006-02-07
forum: Desktop Environments
---

### Post by wacole on 2006-02-07
When attempting to change the configuration on SMB4K (Ubuntu 5.1) - I can't get it to see my network - I receive this error message:

/bin/sh: kdesu : command not found

I'm guessing this is KDE's equiv of SUDO, but I don't know how to correct this.  Clues would be much appreciated.

Thanks,

---

### Post by kaamos on 2006-02-07
just a guess:
```
sudo ln -s /usr/bin/gksudo /usr/bin/kdesu
```
or
```
sudo ln -s /usr/bin/gksu /usr/bin/kdesu
```
Hope this helps.

---

### Post by wacole on 2006-02-07
Thanks very much.  Getting closer.   After I applied the first option, I opened SMB4K, went to configuration, made a change and pressed Apply.

I was asked for my root password which I entered and then received the following error message:
[I]
(kdesu:15014): Gtk-WARNING **: Failed to set label from markup due to error parsing markup: Error on line 1: Character '&' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;[/I]

Hmmm, not sure what this is about.   I think the change to the configuration took (at least it is reflected on the GUI), but I can't be absolutely sure.

Thanks again,

---

