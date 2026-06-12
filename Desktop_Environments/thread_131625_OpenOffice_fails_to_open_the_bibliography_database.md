---
title: "OpenOffice fails to open the bibliography database"
date: 2006-02-16
forum: Desktop Environments
---

### Post by patis on 2006-02-16
Hello,

I'm running OpenOffice.org 2.0.1 on Breezy. When I click **Tools->Bibliography Database** I get a popup window with the following:

[INDENT]The following column names could not be assigned:
    Short name
    Type
    ...
    (several other fields)
    ...
    Do you want to edit the column arrangement?
[/INDENT]

Regardless of how I answer, I cannot input any bibliography entry at all. Seems like a bug to me. Can you verify if you get the same behavior? Can anyone verify with the pre-2.0 version originally shipped with Breezy?

Thanks,

Patis

---

### Post by ronmarley1 on 2006-02-16
Hi Patis,
This is not an answer, but you might want to have a look at the OOo forum at [http://www.oooforum.org/](http://www.oooforum.org/).  If you've already tried this, sorry for the non-answer.

---

### Post by tassou on 2006-02-26
same problem here
I'm looking for a solution but it seems to be related to the 2.0.1 provided by doko as it is not described on many websites.
Actually google gives me links to openoffice source code translation files containing this error message :).
I have been looking on oooforums as well (very good link thank you) with no success.

Thank anyone for help :)

EDIT: see [http://ubuntuforums.org/showthread.php?p=776703#post776703](http://ubuntuforums.org/showthread.php?p=776703#post776703)

---

### Post by proshanto on 2008-05-13
Found it!!!

Install openoffice.org-base. That solved my problem same as you had.

Seems like Ubuntu installs openoffice.org-base-core automatically (speaking about 8.04 Hardy), but that does not open databases. As soon as openoffice.org-base is installed, the bibliography database opened up.

Hope this helps.

---

