---
title: "Using SCIM in KDE programs"
date: 2007-12-28
forum: Desktop Environments
---

### Post by fdimmling on 2007-12-28
I am running Gutsy with scim-bridge to enter Chinese characters, which works fine for Gnome programs and Openoffice but not for KDE programs like Kile. Ctrl-Space does not bring up the Chinese input. 
How can I activate it?

friedrich:confused:

Solution: I had to delete the local .scim directory to make the changes in /etc/xinit/xinput.d/scim effective.

---

