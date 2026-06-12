---
title: "Installing Synaptic Package Manager"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Complitric on 2006-08-13
I have just installed Kubuntu for a 32 bit machine.  It does not seem to have Update Manager nor Synaptic Package Manager.  I would like to get Synaptic installed, but Adept does not offer that, what can I do?

---

### Post by GhostDawg on 2006-08-13
Have you tried typing in a terminal window:

sudo apt-get update
sudo apt-get install synaptic

That should get it working.

---

### Post by Complitric on 2006-08-13
Package synaptic is not available, but is referred to by another package...

Something I need to add to /etc/apt/sources.list?

I have already included Universe.

---

### Post by aysiu on 2006-08-13
Sounds as if you have conflicting repositories.

1. Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. Try again: ```
sudo aptitude update
sudo aptitude install synaptic
```

---

### Post by Complitric on 2006-08-13
That worked, thank you!

---

### Post by drtvasudevan on 2006-08-13
are synaptic and adept mutually exclusive if one has both gde and kde installed?

---

