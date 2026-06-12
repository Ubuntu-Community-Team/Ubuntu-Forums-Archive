---
title: "Thunderbird"
date: 2008-05-04
forum: Desktop Environments
---

### Post by TakeLifeEasy on 2008-05-04
I can only find Thunderbird 2.0.0.12 in the repositories however, Thunderbird 2.0.0.14 is out.  Any ideas when the Ubuntu will list is the repository?

---

### Post by linuxwizard on 2008-05-04
Their should be an update within a few days.

---

### Post by p_quarles on 2008-05-04
> **linuxwizard said:**
> Their should be an update within a few days.
Not necessarily. It really depends on what kinds of changes were made, and whether or not they are crucial for the Ubuntu repackaging. The best way to find out is to check the package on Launchpad. 

Generally speaking, unless a package is shipped in pre-release form (like GIMP 2.4 in Ubuntu 7.10, or Firefox 3.0 in Ubuntu 8.04), it is not updated in the stable repositories. The exceptions are generally only for bugfixes and security patches. 

To enable a wider range of updates, you can enable the Backports repository.

---

### Post by lemuriaX on 2008-05-04
Also there is ubuntuzilla - which seems to be a nice way to update Thunderbird and Firefox if the latest version is not in the repositories.

---

### Post by stinger30au on 2008-05-04
> **lemuriaX said:**
> Also there is ubuntuzilla - which seems to be a nice way to update Thunderbird and Firefox if the latest version is not in the repositories.

here is a link to it

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by TakeLifeEasy on 2008-05-05
Many thanks for all your help guys.  I have now enabled the backports repository and although it does not have Thunderbird in there, it seems a good way to keep on top of all the new software.  I will also have a go at ubuntuzilla as I believe these updates are essential.

Again, many thanks.

---

### Post by p_quarles on 2008-05-06
The Ubuntu security team just announced that Thunderbird has been upgraded to 2.0.0.14, due to an XSS vulnerability. I got this notice via e-mail, but it will be posted to the following forum shortly:
[http://ubuntuforums.org/forumdisplay.php?f=13](http://ubuntuforums.org/forumdisplay.php?f=13)

It's a good idea to keep an eye on that area for announcements concerning packages you use.

For the record, the vulnerability in Thunderbird wouldn't affect anyone who maintains good security practices. The exploit would affect those who clicked on unknown links, *and* had Javascript enabled. That is not a good combination. ;)

---

