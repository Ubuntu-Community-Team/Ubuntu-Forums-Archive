---
title: "download update failed"
date: 2009-02-09
forum: General Help
---

### Post by dizzle.d on 2009-02-09
hello folks, i am useless on computers, am trying to get used to linux (which i am liking lots). this download failed when trying to install, anybody else have this problem? know why?... thanks all, darren

Translation-en_GB.bz2  Could not resolve ‘packages.medibuntu.org’  W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_GB.bz2](http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_GB.bz2)  Could not resolve ‘packages.medibuntu.org’  W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by howefield on 2009-02-09
You sure you have the name of the repository correct ?

looks like it there is some stuff at the end that shouldn't be.

---

### Post by SeanTater on 2009-02-09
It's a DNS error. That site certainly is there, unless an ISP blocked it or the like. 

You should probably just keep running ```
sudo apt-get update
``` every once in a while until it comes back up.

---

### Post by SeanTater on 2009-02-09
Even though that's not the error he was experiencing, that file returns 404. There's no translation for that list. But a 404 would be ignored and it would choose the default translation (AFAIK).

---

### Post by drs305 on 2009-02-09
The problem at present is that the i18n directory for hardy currently doesn't exist on the medibuntu server. I can get as far as *[http://packages.medibuntu.org/dists/hardy/non-free/](http://packages.medibuntu.org/dists/hardy/non-free/)* but the *i18n* directory is not there. (It *is* there for intrepid)

Until it is restored, your best option may be to deselect the checkbox entry for the medibuntu repository in Synaptic or Software Sources (Settings > Repositories > Third-Party.

---

