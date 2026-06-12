---
title: "Making Inconsolata and Minion Pro  visible to OpenOffice"
date: 2009-07-16
forum: Desktop Environments
---

### Post by chandra on 2009-07-16
I have installed the Inconsolata ttf fonts using ```
sudo apt-get install ttf-inconsolata
```

However, this font is not available in OpenOffice under the font selection drop down panel.

Moreover, running
```
sudo fc-cache -v -f
``` and opening OpenOffice after that does not seem to make a difference.

I have also separately installed the Minion Pro otf fonts and  made them available system-wide. But they too are unavailable in OpenOffice.

Thanks in advance.

How do I make these fonts available to OpenOffice?

---

### Post by mcduck on 2009-07-16
have you logged out and back again after installing those fonts? Some programs require that before they recognize newly installed fonts.

---

### Post by chandra on 2009-07-16
> **mcduck said:**
> have you logged out and back again after installing those fonts? Some programs require that before they recognize newly installed fonts.

Yes, indeed.

---

### Post by chandra on 2009-07-27
It appears that the package ttf-inconsolata is making available not a ttf font but in reality an otf font as is apparent by executing ```
dpkg -L ttf-inconsolata
```

The Minion Pro font is also an otf font.

Moreover, it appears that otf fonts are unsupported in OpenOffice.org 3.0 and 3.1, but reasonable workarounds are available. See for example:

[http://www.se.eecs.uni-kassel.de/~thm/OpenOffice.org/bugs.html](http://www.se.eecs.uni-kassel.de/~thm/OpenOffice.org/bugs.html)

[http://linux-wizard.net/index.php?id_blog=142](http://linux-wizard.net/index.php?id_blog=142)

To answer my own question, until otf fonts are supported natively in OpenOffoce.org, it appears that Inconsolata and Minion Pro will not enjoy availability in that suite of software.

---

