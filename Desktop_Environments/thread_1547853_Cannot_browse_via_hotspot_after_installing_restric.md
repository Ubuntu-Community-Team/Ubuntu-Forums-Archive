---
title: "Cannot browse via hotspot after installing restricted-extras"
date: 2010-08-07
forum: Desktop Environments
---

### Post by awe on 2010-08-07
Hi,

I've been searching within the forum but I have not found any thread about this. I hope that I am not repeating a thread.

I can connect successfully to HotSpots in the sense that I can see the network and connect to it. However, I cannot browse. After I open FireFox I am supposed to be brought automatically to the login page, but instead it keeps saying "connecting to..." until it fails with an error message. After researching a bit further, I have found out that this happens when the package *ubuntu-restricted-extras* has been installed. All works perfectly before installing this package. This has been going on for quite a few releases now, I think since 9.04 at least. I have come up with this problem on three completely different computers, so I would say that the hardware is not the problem. This issue also happens with Epiphany and Konqueror, so I presume that it's not a problem with the browser neither.

Rather, it looks to me like one of the many packages that are installed with *ubuntu-restricted-extras* causes the problem.

Any suggestions? Thank you!

---

### Post by lovinglinux on 2010-08-07
Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

This usually fixes such issues. Nevertheless, It's strange that this started to happen after restricted-extras install.

---

### Post by awe on 2010-08-08
Hi, thanks for the help but the problem appears to be something else. And yes, it is very suspicious that it *always* happens after installing *ubuntu-restricted-extras*. I'm pretty sure that one of the many packages that is installed by restricted-extras causes the problem.

Is there any log file that you suggest I should investigate?

Can someone please give me the details of which exact packages does restricted-extras install? Which of these are related to networking?

Thank you all in advance.

---

### Post by lovinglinux on 2010-08-08
Here is the list: [http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

---

### Post by awe on 2010-08-09
It seems that I have found the offending package. I have purged all the IcedTea6 packages (which were installed by *ubuntu-restricted-extras* and I have install sun-java instead. *Et voilà!* I can use HotSpots again.

How, or rather, where can I file a bug request for IcedTea?

---

### Post by lovinglinux on 2010-08-09
> **awe said:**
> It seems that I have found the offending package. I have purged all the IcedTea6 packages (which were installed by *ubuntu-restricted-extras* and I have install sun-java instead. *Et voilà!* I can use HotSpots again.

How, or rather, where can I file a bug request for IcedTea?

Thanks for the heads up.

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

