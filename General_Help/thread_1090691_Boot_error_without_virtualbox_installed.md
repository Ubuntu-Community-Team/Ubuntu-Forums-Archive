---
title: "Boot error without virtualbox installed"
date: 2009-03-08
forum: General Help
---

### Post by Dalamarjj78 on 2009-03-08
While booting my system I receive the message "No suitable module for running kernel found" After browsing the forums the only answers were directed towards those with virtualbox installed on their system.

I, however, have long since removed virtualbox from my system (since I lost all wifi connectivity as soon as the installation was complete and regained my wifi connectivity as soon as virtualbox was removed).

Any ideas how I can resolve this issue (without having to reinstall virtualbox)?

Thanks in advance.

---

### Post by dcstar on 2009-03-08
> **Dalamarjj78 said:**
> While booting my system I receive the message "No suitable module for running kernel found" After browsing the forums the only answers were directed towards those with virtualbox installed on their system.

I, however, have long since removed virtualbox from my system (since I lost all wifi connectivity as soon as the installation was complete and regained my wifi connectivity as soon as virtualbox was removed).

Any ideas how I can resolve this issue (without having to reinstall virtualbox)?

Thanks in advance.

Look in your /etc/modules files for whatever is trying to load the virtualbox modules.

---

