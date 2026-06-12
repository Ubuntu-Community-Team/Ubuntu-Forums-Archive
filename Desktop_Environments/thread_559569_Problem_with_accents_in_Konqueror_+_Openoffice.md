---
title: "Problem with accents in Konqueror + Openoffice"
date: 2007-09-25
forum: Desktop Environments
---

### Post by bestiajo on 2007-09-25
Hello everyone:

First of all, sorry for my bad English! I post from Spain...

I use Ubuntu Feisty, Gnome, Openoffice and Konqueror, and it usually works fine, but if I copy some text in Konqueror and paste it in Openoffice Writer, vowels with accents get replaced by ugly symbols. The problem happens only if I use those two programs. If I copy in Konqueror and paste in Gedit or Openoffice Calc, for example, there is no problem. If I copy in Firefox or Gedit or whatever and paste in OO Writer, it works well too. I have tried to install some i18n and l10n packages (a lot of them, I cannot remember which ones) and the problem did not disappear. Besides, I have searched the web, with no result, so I need the forum's help. If you know, please tell me what I should do. Thank you very much indeed!

Kind regards,
Bestiajo

---

### Post by por100pre1 on 2007-09-25
Try checking if you have these packages installed:

```
sudo apt-get install language-pack-kde-es language-pack-kde-es-base
```

---

### Post by bestiajo on 2007-09-26
Yes, those packages were already installed. That is not the problem. Could it be a bug in Ubuntu  Feisty that should be reported?

---

### Post by magnusbb on 2007-10-14
This is not a Konqueror or KDE related bug; it is OpenOffice Writer's fault. Try doing the copy+paste operation in OpenOffice Calc, and you will see that the diacritical marks appear as they should.

I have filed a bug report in the bug tracking system of OpenOffice.org:
[http://www.openoffice.org/issues/show_bug.cgi?id=82534](http://www.openoffice.org/issues/show_bug.cgi?id=82534)

It would be just magnificent to have this bug fixed, because it has been around for years.

---

