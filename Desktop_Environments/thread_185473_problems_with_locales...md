---
title: "problems with locales.."
date: 2006-05-31
forum: Desktop Environments
---

### Post by ruzkie on 2006-05-31
(random output showing whats wrong, get the same in apt-get or irssi or whatever)

      perl: warning: Setting locale failed.
      perl: warning: Please check that your locale settings:
              LANGUAGE = "en_GB:en",
              LC_ALL = (unset),
              LANG = "en_GB"
          are supported and installed on your system.
      perl: warning: Falling back to the standard locale ("C").
      locale: Cannot set LC_CTYPE to default locale: No such file or directory
      locale: Cannot set LC_MESSAGES to default locale: No such file or directory.
      locale: Cannot set LC_ALL to default locale: No such file or directory

      and i set in /etc/envoriment
      PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11$
      LANG="en_GB.ISO-8859-15"
      LANGUAGE="en_GB:en"
      and do
      ruskie@ruskie-desktop:~$ sudo locale-gen       
      Generating locales...
        en_GB.ISO-8859-15... up-to-date
        en_GB.UTF-8... up-to-date
        en_US.UTF-8... up-to-date
        sv_SE.ISO-8859-15... up-to-date
      Generation complete.

      but still the same.
      just tell me if you need more info or output il glady get this working ;)

---

### Post by ruzkie on 2006-06-01
a

---

