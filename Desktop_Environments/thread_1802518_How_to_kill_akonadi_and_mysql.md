---
title: "How to kill akonadi and mysql?"
date: 2011-07-12
forum: Desktop Environments
---

### Post by uqbar on 2011-07-12
I'm running KDE and am not using any PIM stuff.
I would like to avoid to start akonady and the related mysqld RDBMS.
Any idea? There's nothing in the Settings to handle this.

TIA.

---

### Post by ankspo71 on 2011-07-12
Hi,
If you do not need things such as desktop search, kontact, file labeling and rating, etc, then you probably could disable the desktop search settings to help prevent akonadi and mysql from automatically running in the background. Disabling the desktop search has solved a few different  types of runaway KDE related processes for some people.

Go to System Settings > Desktop Search; then go to the basic settings tab and disable Nepomuk and Strigi. Click Apply.

Here is a link that explains a little on how these KDE applications work together.
[http://thomasmcguire.wordpress.com/2009/10/03/akonadi-nepomuk-and-strigi-explained/](http://thomasmcguire.wordpress.com/2009/10/03/akonadi-nepomuk-and-strigi-explained/)

Hope this helps.

---

