---
title: "Cannot install updates -- Run partial upgrade?"
date: 2008-12-31
forum: General Help
---

### Post by bg1256 on 2008-12-31
For some reason, I cannot install several automatic updates on my system. When I open update manager, I receive the following dialog message:

"Not all updates can be installed.

Run a partial upgrade to install as many updates as possible."

See the screenshots I've attached for exactly what my problem entails.

Because the major part of that update is Open Office, I would really like to get this solved.

And yes, I've run the partial upgrade option, and nothing happens. I've also checked in synaptic to verify that open office is installed from the ubuntu repos, and it is.

Any ideas?

---

### Post by fooman on 2008-12-31
have you tried using synaptic?

if not...open synaptic package manager,  click "reload", then "mark all upgrades"...then "apply"

see if that works.

edit: sorry,  i should have said...have you used synaptic to *update*? ...i can see that you "*checked in synaptic to verify that open office is installed*"....but try using it to run the update and see if that works.

---

### Post by redilyn on 2008-12-31
You may need to run a dist-upgrade

```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

