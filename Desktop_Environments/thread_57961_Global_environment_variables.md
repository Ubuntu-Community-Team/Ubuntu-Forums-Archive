---
title: "Global environment variables?"
date: 2005-08-18
forum: Desktop Environments
---

### Post by kook44 on 2005-08-18
Hi-
How can I set an environmant variable to be used globally?  When I place en export statement in /etc/bash.bashrc, that variable is only valid in instances of the bash terminal.  I need to have an environment variable that is valid for remote logins and apps launched from gnome, as well as the termnal.

Thanks

---

### Post by kook44 on 2005-08-18
bump

---

### Post by professor_chaos on 2005-08-18
found this from google....

I believe that environment variables get set in a login shell script (/etc/profile or ~/.bash_profile) rather than one that gets executed for each terminal session (/etc/bash.bashrc or ~/.bashrc).

---

