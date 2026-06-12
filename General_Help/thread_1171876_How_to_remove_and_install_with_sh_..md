---
title: "How to remove and install with sh ./"
date: 2009-05-27
forum: General Help
---

### Post by norcim on 2009-05-27
I installed an app using the command sh./appname.
sudo apt-get remove appname  does not seem to remove it completely.
Is there another way.

---

### Post by Locutus_of_Borg on 2009-05-27
read through script for what files are installed and delete them if there is not an included uninstall script

also, i take it you are not referring to compiling source, but if you are, a simple 'make uninstall' in the source directory should uninstall everything

---

