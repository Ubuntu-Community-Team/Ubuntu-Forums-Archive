---
title: "Wireless Problems in Ubuntu"
date: 2005-12-21
forum: Desktop Environments
---

### Post by diffuser78 on 2005-12-21
I have couple of issues with wireless. I am sure some of you must have had these issues in past.

1. Wireless internet in Ubuntu is slow as compared to Win XP....I dont know why  ? Wired internet in Ubuntu is as fast or even faster than win xp. Can somebody throw some pointers to fix this.

2. I work at home and my school. I want that whenever I open my laptop it uses the best connections based on the preferences which I give. For example while booting at home it should automatically take my home wireless network and whle I am at school it should automatically take the school's wireless address. (I use WEP key at my home to guard my connection while at School its an open internet).

Can I do the above mentioned thing by editing some file in Ubuntu.

Any help is appreciated,

Thanks

---

### Post by zoiks on 2005-12-21
waproamd might be what you are looking for.  It's in the repositories.  From the description:

[I]WLAN roaming daemon
waproamd is a Linux WLAN roaming daemon for IEEE 802.11
cards supported by a driver with wireless extension API. It may be
used for configuring WEP keys according to the WLANs available, and
automatically configures the network interface when an access point is
found.

This version does not need ifplugd any more to configure the network
card.[/I]

---

### Post by diffuser78 on 2005-12-21
I will try ths one.

I was wondering if it can be done with ease. Whenever I open my laptop it takes the best connection.

Is there a way, we can disable network detection during booting. What happens is if my wireless network is not working my lappy takes 3 minutes to boot.

thanks

---

### Post by dafrabbit on 2005-12-21
What you're asking for may be in place for Dapper. You're basically asking for inclusion of NetworkManager I believe.

In terms of disabling network connection, you can either ctrl-c whenever it starts detecting network during booting to skip that part. Or once you boot into ubuntu, go to System->Administration->Networking. Select your wireless connection, click properties and uncheck the box for "enable this connection". Keep in mind that this means having to manually activate your connection every time you boot up....

---

### Post by diffuser78 on 2005-12-22
is there any network manager avaialbe in breezy ?

I want my laptop to have internet whenever i open it. Please help

---

