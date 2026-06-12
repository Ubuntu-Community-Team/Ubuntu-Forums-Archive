---
title: "Synaptic Error"
date: 2006-01-11
forum: General Help
---

### Post by seekyrr on 2006-01-11
When I try to enable the extra repositories I get this error trying to refresh.

[B]W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: Unknown error executing gpgv
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release: Unknown error executing gpgv
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release: Unknown error executing gpgv
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-backports Release: Unknown error executing gpgv[/B]

If I go and manualy uncomment the sections it still doesnt work.

I tried this.. but still getting errors.

[B]sudo apt-get --purge remove synaptic

then

sudo apt-get update

sudo apt-get install synaptic

sudo apt-get clean

sudo update-menus[/B]

I tired to use Synaptic to reinstall itself from CD...but same probs.

Any advice would be appreciated.

Thanks

---

### Post by aysiu on 2006-01-13
Can you post your /etc/apt/sources.list?

---

