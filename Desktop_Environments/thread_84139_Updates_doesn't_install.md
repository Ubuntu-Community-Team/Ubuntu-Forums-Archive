---
title: "Updates doesn't install"
date: 2005-10-30
forum: Desktop Environments
---

### Post by Diego F. on 2005-10-30
Hi. I'm having a problem with updates. I get a message with the advise of new updates, but when try to install them, it shows for a second the download window and closes it again.

I try unselecting some of the updates and once I could install one, but I can't skip the problem with the others.

Did someone meet that problem?

---

### Post by Xian on 2005-10-30
Do the update session in a terminal so you can catch the error message (if indeed there is a problem). From the main panel goto Applications > Accessories > Teminal. Enter the command below:

```
$ sudo apt-get dist-upgrade
```

---

### Post by NewbieNik on 2005-10-30
[QUOTE=Diego F.]Hi. I'm having a problem with updates. I get a message with the advise of new updates, but when try to install them, it shows for a second the download window and closes it again.

I try unselecting some of the updates and once I could install one, but I can't skip the problem with the others.

Did someone meet that problem?[/QUOTE]


Try running a "sudo apt-get update" command to ensure the synaptic is connecting to the repos.
then try "sudo apt-get -f install" to fix any errors and the "sudo apt-get upgrade" to upgrade. Make sure you have closed the update manager window!!

---

