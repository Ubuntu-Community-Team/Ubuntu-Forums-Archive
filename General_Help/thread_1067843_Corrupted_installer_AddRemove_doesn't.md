---
title: "Corrupted installer? Add/Remove doesn't"
date: 2009-02-12
forum: General Help
---

### Post by Cloggsy on 2009-02-12
My Add/Remove Applications doesn't.

If I click on it then the application starts and searches for installed and available applications as per normal but then comes back blank showing no applications and the message: "There is no matching application available"

Synaptic still lists packages and I have no reason to suspect it is no longer working.

I suspect some sort of catalogue has become corrupted - help please...

---

### Post by kostkon on 2009-02-12
Try reinstalling it either using *Synaptic* (search for the *gnome-app-install* package and mark it for reinstallation) or in a terminal give
```
sudo apt-get install gnome-app-install --reinstall
```

---

### Post by Cloggsy on 2009-02-12
Bingo!

Also reinstalled the data application as a precaution

Thank you

---

