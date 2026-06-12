---
title: "On updating programs..."
date: 2006-08-14
forum: Desktop Environments
---

### Post by statue on 2006-08-14
How does one go about updating programs within Ubuntu? Is it cli only or is there a GUI I could use? Currently I'm trying to update Apache as while it is working fine, its not the latest release and I would prefer to update it for security reasons. Thanks

---

### Post by az on 2006-08-14
> **statue said:**
> How does one go about updating programs within Ubuntu? Is it cli only or is there a GUI I could use? Currently I'm trying to update Apache as while it is working fine, its not the latest release and I would prefer to update it for security reasons. Thanks

Use any package manager.  If you are using the desktop, use the update-manager.  Make sure that the security and updates repositories are enabled (dapper main, dapper-updates main, dapper-security main, etc...)

You will get a popup when there are security updates.

From the command line, edit your /etc/apt/sources.list to include all those repos (they are enabled by default) and run

sudo apt-get update

sudo apt-get upgrade

The very latest cutting-edge version of apache2 is not in the repositories.  For security reasons, the stable version is in Dapper.  Perhpas Edgy will contain the very latest stable version of Apache2 when it is released.  But if you want security, stick with what is in the repos.

---

