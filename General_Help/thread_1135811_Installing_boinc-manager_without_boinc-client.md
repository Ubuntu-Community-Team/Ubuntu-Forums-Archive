---
title: "Installing boinc-manager without boinc-client"
date: 2009-04-24
forum: General Help
---

### Post by mcguire on 2009-04-24
Hi,

I would like to know if there is a clean way to install boinc-manager package without installing boinc-client package.

apt-get install boinc-manager also install boinc-client as a dependency. But, when I check boinc-manager package with the dpkg -I command, boinc-client only appears as recommended.

So, is there a way to tell apt-get to not install recommended packages?

---

### Post by dcstar on 2009-04-24
> **mcguire said:**
> Hi,

I would like to know if there is a clean way to install boinc-manager package without installing boinc-client package.

apt-get install boinc-manager also install boinc-client as a dependency. But, when I check boinc-manager package with the dpkg -I command, boinc-client only appears as recommended.

So, is there a way to tell apt-get to not install recommended packages?

Synaptic has an option to install recommend packages or not, turn it off and use that.

---

