---
title: "Configuring multiple workstations"
date: 2006-03-15
forum: Desktop Environments
---

### Post by nocturn on 2006-03-15
I'm looking for a solution to keep multiple workstations on the same configuration.

I want do change a number of files, like /etc/pam.d/* and some stuff in /etc/security/*

What would be the best way to handle this?

I'm considering:
- a script that runs during boot and downloads new files if it is on the local network
- A local repository with a package that replaces default config files (will this create conflicts with the owning packages?)
- Any other suggestions?

---

