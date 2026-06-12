---
title: "Can I disable from starting zeitgeist datahub ?"
date: 2012-09-30
forum: Desktop Environments
---

### Post by claracc on 2012-09-30
I am using gnome fallback desktop in my ubuntu 12.04.01 system.

Can I disable from starting at the beginning zeitgeist datahub (remark, I don't use unity) in order to get a quicker boot?, ¿can it result in some undesired side effect ?

Thanks in advance.

---

### Post by germanix on 2012-09-30
I used synaptic package manager to completely remove Zeitgeist and I have not seen any negative side effects for me. I do not like zeitgeist and do not use it, so I removed it right after I installed 12.04. I do not know if this made the boot process any faster or not, this was not the issue for me. I just wanted it gone.

---

### Post by jerrrys on 2012-09-30
According to the [manpage ]("http://manpages.ubuntu.com/manpages/precise/man1/zeitgeist-datahub.1.html")there are no options available.[FONT=monospace][B]  But found this.

[http://ubuntuforums.org/showthread.php?p=10892713](http://ubuntuforums.org/showthread.php?p=10892713)
[/B][/FONT]

---

### Post by 2F4U on 2012-09-30
> **claracc said:**
> I am using gnome fallback desktop in my ubuntu 12.04.01 system.

Can I disable from starting at the beginning zeitgeist datahub (remark, I don't use unity) in order to get a quicker boot?, ¿can it result in some undesired side effect ?

Thanks in advance.

Do you have the privacy manager for zeitgeist on your system? If yes, you can turn off almost all activity logging.

[http://milky.manishsinha.net/2012/02/07/privacy-and-activity-manager-zeitgeist-release/](http://milky.manishsinha.net/2012/02/07/privacy-and-activity-manager-zeitgeist-release/)

You can also remove the zeitgeist-datahub from the automatically started applications.

---

### Post by claracc on 2012-09-30
> **2F4U said:**
> Do you have the privacy manager for zeitgeist on your system? If yes, you can turn off almost all activity logging.

[http://milky.manishsinha.net/2012/02/07/privacy-and-activity-manager-zeitgeist-release/](http://milky.manishsinha.net/2012/02/07/privacy-and-activity-manager-zeitgeist-release/)

You can also remove the zeitgeist-datahub from the automatically started applications.

Yes I have privacy, but I haven't ever used or configured. I am going to turn off the logging activity and disable zeitgeist-datahub from starting apps. As I have read in one of the links of the answers it can do quicker the boot time.

The answers have been very useful, now I know what for is zeitgeist.

Thanks to all

---

### Post by claracc on 2012-10-01
I have disabled both privacy ( not to register activity )and zeitergaist datahub, no side effects, but unfortunately I haven't got reducing the boot time of my laptop (50 seconds from selecting kernel in grub till login page is shown), and about thirty seconds more since I introduce password in login page till desktop can be used.

---

