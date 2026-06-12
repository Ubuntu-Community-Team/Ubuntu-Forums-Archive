---
title: "[ubuntu] freeipa cleint 4.10.1"
date: 2023-01-23
forum: Desktop Environments
---

### Post by se2a on 2023-01-23
Morning All,

**FreeIPA** recently introduced freeipa 4.10.1 -> [https://www.freeipa.org/page/Releases/4.10.1](https://www.freeipa.org/page/Releases/4.10.1)

which has interesting feature developed:

> 
[LIST]
[*]8803: Add support for managing IdP references 
[/LIST]
 FreeIPA can now authenticate users with the help of  OAuth 2.0 identity providers supporting OAuth 2.0 Device Authorization  Flow. IdPs known to work are Keycloak, Microsoft Azure, Google, Github,  and Okta. Details on how to use Keycloak can be found in FreeIPA  workshop: [https://freeipa.readthedocs.io/en/latest/workshop/12-external-idp-support.html](https://freeipa.readthedocs.io/en/latest/workshop/12-external-idp-support.html)


and it is working fine with **Fedora 37+**, I  was able to run whole process with successful login into **Azure AD**. Do you know Guys where I can ask for help for the same according to **Ubuntu**.

I already tried to do similar with **Ubuntu 23.04**, as there is the newest version [COLOR=#333333][FONT=&amp] **freeipa-client_4.9.11-1_amd64.deb** ([https://packages.ubuntu.com/lunar/amd64/freeipa-client/download](https://packages.ubuntu.com/lunar/amd64/freeipa-client/download)), which also has the same statement in release notes -> [https://www.freeipa.org/page/Releases/4.9.10](https://www.freeipa.org/page/Releases/4.9.10)

[/FONT][/COLOR]> 
[LIST]
[*]8803: Add support for managing IdP references 
[/LIST]
 FreeIPA can now authenticate users with the help of  OAuth 2.0 identity providers supporting OAuth 2.0 Device Authorization  Flow. IdPs known to work are Keycloak, Microsoft Azure, Google, Github,  and Okta. Details on how to use Keycloak can be found in FreeIPA  workshop: [https://freeipa.readthedocs.io/en/latest/workshop/12-external-idp-support.html](https://freeipa.readthedocs.io/en/latest/workshop/12-external-idp-support.html)
[COLOR=#333333][FONT=&amp]

but sadly it doesn't allows me to replicate a flow from** Fedora 37**+. As I already get a response from Fedora maintainers -> [https://lists.fedorahosted.org/archives/list/freeipa-users@lists.fedorahosted.org/thread/SEKD5MXYJLOE3TZ25QHFTLLHX2BVMH5G/](https://lists.fedorahosted.org/archives/list/freeipa-users@lists.fedorahosted.org/thread/SEKD5MXYJLOE3TZ25QHFTLLHX2BVMH5G/)

there could be some differences between packages for particular distros, so my question is if any of us already tried to connect **Azure AD** with [B]FreeIPA.

[/B]My current setup on Ubuntu 23.04 is:
 
- sssd --version
2.7.3

[/FONT][/COLOR]- ipa --version
VERSION: 4.9.11, API_VERSION: 2.251

if any of you have any experience with it and will be happy to share feel free. Otherwise maybe someone knows where I  can find an info when version 4.10.1 of FreeIPA will be announced for ubuntu / debian distros.

BR

---

### Post by TheFu on 2023-01-23
This thread needs to be in the pre-release "Ubuntu Development Version" forum.
23.04 isn't released ... uh ... until April.

I'd just be happy if Ubuntu made connecting to an ubuntu-based LDAP trivial, so we don't need any MS junk.  The normal user managment built into every Ubuntu should be using an LDAP back-end, local if not centralized. It is a bit embarrassing NOT to have LDAP as the default for users/groups/host management Ubuntu desktops and servers.  Basically, LDAP should be a complete replacement for NIS and trivial/automatic in the installations for all Ubuntu desktop flavors.

---

