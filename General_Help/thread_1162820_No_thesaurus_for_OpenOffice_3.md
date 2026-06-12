---
title: "No thesaurus for OpenOffice 3"
date: 2009-05-18
forum: General Help
---

### Post by monsterstack on 2009-05-18
I'm running OpenOffice 3.0.1 on Jaunty, and I don't seem to have the thesaurus option. I had it with OpenOffice 2.x series, but now the option to get the thesaurus in the "tools" menu is completely greyed out. What is going on here?

A look at my sources.list tells me the following,

```
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main # disabled on upgrade to jaunty
```

But leaving this uncommented makes my system complain.

Apt also tells me that "openoffice.org-thesaurus-en-us is already the newest version."

Can anyone help me out? :S

---

### Post by Arup on 2009-05-18
If you upgraded to OO 3.1 via the ppa, few of the packages are discarded and have to be re-installed back. OO 3.0 which comes standard in Jaunty has the Thesarus as well.

---

### Post by monsterstack on 2009-05-18
All righty. I ran this:

```
sudo apt-get remove --purge openoffice.org*.*
```

to completely nuke OpenOffice. Then I ran this to get it back again,

```
sudo apt-get install openoffice.org
```

But that didn't seem to work. So I installed some of the recommended packages too.

```
sudo apt-get install ispell jed-extra hunspell-en-us myspell-en-gb openoffice.org-help-en-gb openoffice.org-l10n-en-gb openoffice.org-hyphenation openoffice.org-thesaurus-en-au openoffice.org-gnome openoffice.org-kde openclipart-openoffice.org libmyodbc odbc-postgresql libsqliteodbc tdsodbc mdbtools libmysql-java libpg-java openoffice.org-gcj openoffice.org-report-builder openoffice.org-style-industrial
```

Still no success. I don't get it. :(

---

