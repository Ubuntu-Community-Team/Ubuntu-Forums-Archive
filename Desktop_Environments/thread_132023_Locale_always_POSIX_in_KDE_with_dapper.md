---
title: "Locale always POSIX in KDE with dapper"
date: 2006-02-17
forum: Desktop Environments
---

### Post by supermihi on 2006-02-17
I installed dapper flight 3 yesterday and want to have a german system, so I installed all language-pack-de, language-support-de, kde-i18n-de and so on.
The locale (de_DE.UTF-8) was generated and when I log on to a console, the "locale" command shows that everything is set to my locale. However, in KDE the locale is Posix, even though I set everything to german in the control center. In /etc/environment there are also the right settings. The KDE programs are partially german, but firefox, for example, is still in english. Also, every program I launch from konsole is started with the POSIX language. How can this be fixed?
I tried dpkg-reconfigure locales without success.

---

