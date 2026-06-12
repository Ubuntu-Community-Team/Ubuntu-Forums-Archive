---
title: "Ubuntu keeps trying to install exim!"
date: 2009-01-11
forum: General Help
---

### Post by cbraxton on 2009-01-11
I have a Ubuntu 8.10 system on which the Citadel groupware program has been installed via Citadel's "Easy Install" method. (Yes, I know Citadel binaries are in the repositories, but I wanted more control over the installation as well as the ability to obtain Citadel updates after Ubuntu drops 8.10 support.)

The problem I'm having now is that any time I try to install any kind of mail utility via apt-get or Synaptic, Ubuntu insists it wants to install exim4. (Since Citadel is already doing smtp server duty this is obviously not wanted!)

How can I inform the package manager that there is already an MTA installed so as to avoid this problem?

---

