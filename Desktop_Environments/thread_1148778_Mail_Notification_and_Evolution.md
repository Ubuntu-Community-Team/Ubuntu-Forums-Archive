---
title: "Mail Notification and Evolution"
date: 2009-05-04
forum: Desktop Environments
---

### Post by frankabel on 2009-05-04
Hi all,

When try configure and "Add a Mailbox" and select "Evolution" the following message appear.

"
Mail Notification can not contact Evolution. Make sure that Evolution is running and that the Evolution Jean-Yves Lefort's Mail Notification plugin is loaded.
"

What can I do?

Cheers
Frank Abel

---

### Post by khelben1979 on 2009-05-04
You really should try to explain more in detail how you do this so it gets easier to understand what you are doing wrong, but my guess right now is that Evolution isn't installed in the system, and if this is the case:

```
sudo apt-get install evolution
```

---

### Post by frankabel on 2009-05-04
Thanks for your quick reply.

My 9.04 installation is pretty standard, no rare removal/additions or customization. So evolution is installed as per default in Ubuntu.

After install "mail-notification-evolution" and go "App->Internet->Mail Notification" and then "Add" and select "Evolution" the message "
Mail Notification can not contact Evolution. Make sure that Evolution is running and that the Evolution Jean-Yves Lefort's Mail Notification plugin is loaded." show.

Cheers
Frank Abel

---

### Post by khelben1979 on 2009-05-04
Have you tried to activate this feature within the Evolution mail program instead?

---

### Post by frankabel on 2009-05-04
Isn't the same, Evolution notification plugin isn't so feature rich as "Mail Notification" is.

---

### Post by sam_delta on 2009-05-05
some problem here, seems like mail-notification its not able to contact evolution

Sam

---

### Post by andrewski on 2009-05-29
Seems like a bug: [https://bugs.launchpad.net/mail-notification/+bug/376812](https://bugs.launchpad.net/mail-notification/+bug/376812)

---

