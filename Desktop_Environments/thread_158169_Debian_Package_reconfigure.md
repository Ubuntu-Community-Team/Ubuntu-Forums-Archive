---
title: "Debian Package reconfigure"
date: 2006-04-10
forum: Desktop Environments
---

### Post by bitoiu on 2006-04-10
Hi guys,

I'm making an installer for a web service that needs suexec support. Like Adam told me in a post regarding suexec, i can do something like:

dpkg-reconfigure apache
or
dpkg-reconfigure apache2

and then tell graphical interface that I want suexec support.

The thing i'd like to know if there's a command that lets me do this in a way that no questions are asked and no interfaces are shown, like for example:

dpkg-reconfigure "apache suexec"
or 
dpkg-reconfigure "apache2 suexec"

Ovecourse this isn't it. But for installer purposes I need a command that reconfigure's apache with suexec support but with no dialog, like thinking in terms of script i'd like to do this:
....
if ( apache -V no suexec line)
    "reconfigure apache with suexec support"
    "a2enmod suexec"

and that's it. 

Thank you very much, regards to adam who enabled me to get this to work with apache2, since it doesn't prompt any dialog.

---

