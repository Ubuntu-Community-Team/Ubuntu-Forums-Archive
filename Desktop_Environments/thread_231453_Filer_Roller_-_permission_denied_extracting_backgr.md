---
title: "Filer Roller - permission denied extracting backgrounds to /usr/share/backgrounds"
date: 2006-08-07
forum: Desktop Environments
---

### Post by kvalis on 2006-08-07
I am trying to personalize my desktop by adding new wallpapers.

How can I change the permissions in File Roller to be able to extract to the directory I want. Opened a terminal and typed **sudo -i**, and thought that might help, but it did not.

I noticed there was a text box in File Roller for your password - but it was grayed out.

Any suggestions?

Kvalis

---

### Post by Ramses de Norre on 2006-08-07
Open fileroller with ```
gksudo file-roller
``` or use ```
sudo tar xvf
``` from the command line (if it's a tar archive, add g option for .tar.gz or j for .tar.bz2)

---

