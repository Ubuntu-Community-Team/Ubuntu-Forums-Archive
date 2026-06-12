---
title: "installing and replacing ttf-fonts in Ubuntu 14.10"
date: 2015-02-18
forum: Desktop Environments
---

### Post by ernsttremel on 2015-02-18
Hallo,

in früheren Versionren waren selbsterstellte Fonts im Ordner persönlicherOrdner/.fonts installiert. Dort ist aber der gesuchte Font nicht mehr zu finden.

Wie kann ich also einen Font durch den verbesserten Font ersetzen?


Hello,

in former Ubuntu versions there it was possible to install selfmade ttf-fonts into home/user/.fonts or remove them from there to replace them by newer ttf-font's vesions.

Hoe to do this (installing or replacing) in Ubuntu 14.10?

---

### Post by ajgreeny on 2015-02-18
Does it not work in 14.10 as well as the previous versions?  I did not think there had been changes in that arrangement.

Fonts would be more useful to all users if copied into a folder in /usr/share/fonts/truetype/ such as** /usr/share/fonts/truetype/myfonts** which you will have to make yourself with ```
sudo mkdir  /usr/share/fonts/truetype/myfonts
```then run ```
sudo fc-cache -f -v
``` to update the font cache.  All fonts in that folder will be available to all users on the computer; those in a user's own ~/.fonts folder will be available only to that user, not any others.

---

### Post by grahammechanical on 2015-02-18
Have you tried right clicking the font and selecting "Open with Font Viewer" and then click Install font? /home does not have a usr directory but there is a /home/.local/share/ directory where a font installed by the user using font viewer will get copied to.

Regards

---

### Post by ernsttremel on 2015-02-18
> **grahammechanical said:**
> Have you tried right clicking the font and selecting "Open with Font Viewer" and then click Install font? /home does not have a usr directory but there is a /home/.local/share/ directory where a font installed by the user using font viewer will get copied to.

Regards

Thank you very much!
That's it. There I could find my installed fonts as you described in "right clicking the font and selecting "Open with Font Viewer" and then click Install font"

---

