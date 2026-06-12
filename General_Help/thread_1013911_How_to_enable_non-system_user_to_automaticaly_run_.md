---
title: "How to enable non-system user to automaticaly run Update Manager"
date: 2008-12-17
forum: General Help
---

### Post by abcuser on 2008-12-17
Hi,
on home PC are multiple users defined for my family. But I work on this computer lets say once per month. All other family members use computer daily. I only have "sudo" privilege to install system updates from System | Administration | Update Manager.

Is there any way to download & install updates automatically when other non-system user is logged in. Something like on Windows: Automatically download & install updates? Is this possible without user intervention. My family users are not very well computer educated, so installing without asking would be the best approach. Can it be done?
Thanks

---

### Post by Titan8990 on 2008-12-17
Yes, I'm not sure if there is an easier way, but you can set up a root cron job.

The script would look like this:

```
#!/usr/bin/bash

apt-get dist-upgrade
```


Then you could set that script up as a root cron job to run once a week or so.

---

### Post by Slim Odds on 2008-12-17
you don't want "apt-get dist-upgrade"

you want "apt-get -y update && apt-get -y upgrade"

---

### Post by Titan8990 on 2008-12-17
It is your choice between the two. I use dist-upgrade because it will download new kernels in times that regular upgrade will not.

---

### Post by Onesimus on 2008-12-17
Isn't there something built into Update Manager that will do this automatically (?)

If you select System->Administration->Software Sources and then select the Updates tab.  Then select the 'Install security updates without confirmation'

Done.

---

### Post by Slim Odds on 2008-12-17
> **Titan8990 said:**
> It is your choice between the two. I use dist-upgrade because it will download new kernels in times that regular upgrade will not.

Which is probably not what you want to happen while regular users are active on the machine.

He would probably want to do that himself, when he's ready.

---

### Post by roshanjose on 2008-12-17
that's the easiest approach what onesimus has said

---

