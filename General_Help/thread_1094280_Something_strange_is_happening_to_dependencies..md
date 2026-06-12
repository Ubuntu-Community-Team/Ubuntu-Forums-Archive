---
title: "Something strange is happening to dependencies."
date: 2009-03-12
forum: General Help
---

### Post by Julita on 2009-03-12
When I try to install new .deb packages, the system says that dependencies are not satisfied and gives the list of libraries that I have to install. The major problem is that they have already been installed (Synaptic shows it). Re-installation does not help. Is there a way to fix this?

---

### Post by whoop on 2009-03-12
Maybe the dependencies have a version conflict? Like they need older or newer versions of the dependency?

---

### Post by Julita on 2009-03-12
No, they need exactly those versions that have been already installed... i presume that I did something wrong to the system, getting rid of the packages that I did not needed... I mean, those of qt and maybe some others... I wish I knew which library is "responsible" for those issues...

---

### Post by Thelasko on 2009-03-12
What .deb are you trying to install?

---

### Post by Julita on 2009-03-12
Openoffice.org language pack and new version of evince.

---

### Post by Thelasko on 2009-03-12
Well, evince is highly tied to Gnome.  I wouldn't try installing a new version unless an update comes through for it.

Latvian language pack for OpenOffice should be:
```
sudo apt-get install openoffice.org-l10n-lv
```

[Please note:]("http://packages.ubuntu.com/intrepid/openoffice.org-l10n-lv")
> Spelling dictionaries, hyphenation patterns, thesauri and help are not included in this package. There are some available in separate packages (myspell-*, openoffice.org-hyphenation-*, openoffice.org-thesaurus-*, openoffice.org-help-*)

---

### Post by Julita on 2009-03-12
Thank you very much, but I'll continue to compile programs (I have already compiled a new version of qt, xfce 4.6, gimp, pidgin, claws-mail etc...; performance of those programs installed for my architecture is better).

---

### Post by Thelasko on 2009-03-12
> **Julita said:**
> Thank you very much, but I'll continue to compile programs (I have already compiled a new version of qt, xfce 4.6, gimp, pidgin, claws-mail etc...; performance of those programs installed for my architecture is better).

Maybe Ubuntu isn't the right operating system for you...

---

### Post by Julita on 2009-03-12
I got used to it...

---

### Post by Thelasko on 2009-03-12
Well, if you really must compile from source, [http://packages.ubuntu.com/](http://packages.ubuntu.com/) has the source files of most of the packages in the repositories.

---

