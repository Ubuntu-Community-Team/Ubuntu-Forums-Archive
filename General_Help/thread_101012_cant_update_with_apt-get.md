---
title: "cant update with apt-get"
date: 2005-12-08
forum: General Help
---

### Post by twigboy on 2005-12-08
Hi all
when ever I try to update to install a package I get this error at the end.  Why am I not being able to run the update?  I have also done the update with root and still no success. Thanx for your help.


E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Bachstelze on 2005-12-08
don't you have Synaptic open ?

---

### Post by taurus on 2005-12-08
Do you run the update from a terminal or using synaptic?  Make sure synaptic is not running in the background when you run "sudo apt-get update..."

---

### Post by raublekick on 2005-12-08
Yeah looks like you either have synaptic or apt-get running. Synaptic, apt-get, or update manager can only be run exclusively, so only one those three.

---

### Post by twigboy on 2005-12-08
wow thanx for the fast replies.  i am running this fromthe terminal and synaptic is not open.

---

### Post by Bachstelze on 2005-12-08
maybe you have the update manager running in the background. Check with the System monitor.

---

### Post by twigboy on 2005-12-08
what is the name of the processes i should be looking for?

---

