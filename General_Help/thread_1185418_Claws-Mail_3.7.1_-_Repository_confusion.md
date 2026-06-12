---
title: "Claws-Mail 3.7.1 - Repository confusion?"
date: 2009-06-12
forum: General Help
---

### Post by elektronaut on 2009-06-12
Hi,

a while ago I added the [PPA repository for Claws Mail](http://ppa.launchpad.net/claws-mail) to my sources list and installed Claws Mail 3.7.1. Now I'd like to add the S/MIME plugin. But surprisingly through apt-get I now can only get version 3.6.1-1ubuntu1. Everything from the Claws Mail team now has this version number in the package management overview. 'apt-get update' doesn't help. How can I tell apt-get to take the packages from the PPA repository again?

---

### Post by elektronaut on 2009-06-18
Strange. Not sure what happened, but I can get the 3.7.1 versions again. It's still confusing that 'apt-cache show' shows both versions, but that seems to be the way it works - showing all versions of a package in all repositories in use. So I'm shown the official Ubuntu version alongside the PPA version.

---

