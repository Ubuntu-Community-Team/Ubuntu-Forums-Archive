---
title: "acpid log reporting same entry 20 times per second! = huge log file"
date: 2006-01-10
forum: General Help
---

### Post by zi99y on 2006-01-10
While learning the ropes on Ubuntu I've discovered a massive log file
```
/var/log/acpid
```
contains the following entry around 20 times per second
```
[Tue Jan 10 18:36:04 2006] END HANDLER MESSAGES
[Tue Jan 10 18:36:04 2006] action exited with status 0
[Tue Jan 10 18:36:04 2006] completed event "button/lid LID 00000080 00082f5e"
[Tue Jan 10 18:36:04 2006] received event "button/lid LID 00000080 00082f5f"
[Tue Jan 10 18:36:04 2006] notifying client 7557[111:111]
[Tue Jan 10 18:36:04 2006] executing action "/etc/acpi/actions/lm_lid.sh button/lid LID 00000080 00082f5f"
[Tue Jan 10 18:36:04 2006] BEGIN HANDLER MESSAGES
Laptop mode was already disabled, not disabling.
[Tue Jan 10 18:36:04 2006] END HANDLER MESSAGES
[Tue Jan 10 18:36:04 2006] action exited with status 0
[Tue Jan 10 18:36:04 2006] completed event "button/lid LID 00000080 00082f5f"
[Tue Jan 10 18:36:04 2006] received event "button/lid LID 00000080 00082f60"
[Tue Jan 10 18:36:04 2006] notifying client 7557[111:111]
[Tue Jan 10 18:36:04 2006] executing action "/etc/acpi/actions/lm_lid.sh button/lid LID 00000080 00082f60"
[Tue Jan 10 18:36:04 2006] BEGIN HANDLER MESSAGES
Laptop mode was already disabled, not disabling.

```
Now, everything seems to work ok but the logfile has become over 2Gb in size so I would like to fix it!

Any ideas folks?

---

### Post by zi99y on 2006-01-12
Well I deleted the offending log file of 2 Gigabytes, and in a short space of time it's created a new on and stretched to 12.1Mb!!!

Anyone give me a few hints please?!! It's all the same error as above

---

### Post by kaamos on 2006-01-12
You could try disabling acpi. Other than that, I have no suggestions..

---

### Post by Buffalo Soldier on 2006-01-12
are you using a laptop? this is just a wild wild wild guess.... could it be something like ACPI is detecting you're closing your laptop lid, but in fact you're not... so it sends out this bonkers error message.

...just a wild wild wild guess... i just woke up a few minutes ago.

---

### Post by ranf on 2006-01-12
[QUOTE=zi99y]
```
/var/log/acpid
```
contains the following entry around 20 times per second
```
[Tue Jan 10 18:36:04 2006] END HANDLER MESSAGES
[Tue Jan 10 18:36:04 2006] executing action "/etc/acpi/actions/lm_lid.sh button/lid LID 00000080 00082f5f"

```
[/QUOTE]
lm_lid.sh does not come with Breezy.
Did you follow a Hoary Howto? 
(I think there is something in the Wiki)

---

### Post by Arthur Archnix on 2008-05-19
Does anyone know how to disable acpid logging? The manual suggests you can change the default log file. People on launchpad have suggested that you could redirect to dev null. But I haven't been able to figure this out.

---

### Post by Arthur Archnix on 2008-05-26
Debian user Felix Hagemann was kind enough to pass along the solution to me via email, and hopefully he doesn't mind being credited and me sharing his tip here.

To disabled ACPID logging in Ubuntu Hardy Heron you need to add "-l /dev/null" to its startup options located in the config file /etc/default/acpid. So you would open it with:
```
gksudo gedit /etc/default/acpid
```
Then change this line:
```
OPTIONS="-s /var/run/acpid.socket"
```
To this:
```
OPTIONS="-s /var/run/acpid.socket -l /dev/null"
```
Generally speaking, if you don't look at the acpid log then you don't need it running. Ubuntu installs logrotate by default, so its not like the log will grow to massive proportions and take up hard-drive space, however, some have suggested that overly verbose logging by acpid contributes to unecessary disk activity and can prevent laptops from parking the hard-drive head for any significant amount of time. There are bugs to this effect linked to by UbuntuDemon in his threads on the laptop load/cycle count issue that affects many laptop hard-drives.

---

