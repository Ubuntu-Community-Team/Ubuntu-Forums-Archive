---
title: "When will Ubuntu Pro support kernel Linux 5.19.0-46-generic #47~22.04.1-Ubuntu"
date: 2023-07-14
forum: Desktop Environments
---

### Post by mylesmorales1940 on 2023-07-14
Hello,

I want to activate Livepatch for Ubuntu Pro but I received the following:

sudo pro status
SERVICE          ENTITLED  STATUS    DESCRIPTION
esm-apps         yes       enabled   Expanded Security Maintenance for Applications
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
livepatch        yes       warning   Current kernel is not supported
realtime-kernel* yes       disabled  Ubuntu kernel with PREEMPT_RT patches integrated
usg              yes       disabled  Security compliance and audit tools

When will Ubuntu Pro support the following kernel:

Linux 5.19.0-46-generic #47~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Wed Jun 21 15:35:31 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by deadflowr on 2023-07-14
Livepatch? 5.19? Never.

However, livepatch will begin supporting the HWE kernel stacks starting later this month.

That will coincide with the upgrade to the 6.2 kernel stack.

Reference: [https://ubuntu.com/blog/canonical-livepatch-gets-even-better-now-supporting-hardware-enablement-kernels]("https://ubuntu.com/blog/canonical-livepatch-gets-even-better-now-supporting-hardware-enablement-kernels")

---

### Post by #&amp;thj^% on 2023-07-14
> **deadflowr said:**
> Livepatch? 5.19? Never.

However, livepatch will begin supporting the HWE kernel stacks starting later this month.

That will coincide with the upgrade to the 6.2 kernel stack.

Reference: [https://ubuntu.com/blog/canonical-livepatch-gets-even-better-now-supporting-hardware-enablement-kernels]("https://ubuntu.com/blog/canonical-livepatch-gets-even-better-now-supporting-hardware-enablement-kernels")
Great Info and +1
Two choices:
```
linux-image-generic-hwe-22.04-edge | 5.19.0.21.21          | kinetic          | amd64, arm64, armhf, ppc64el, s390x
 linux-image-generic-hwe-22.04-edge | 5.19.0.43.44~22.04.17 | jammy-security   | amd64, arm64, armhf, ppc64el, s390x
 linux-image-generic-hwe-22.04-edge | 5.19.0.43.44~22.04.17 | jammy-updates    | amd64, arm64, armhf, ppc64el, s390x

```
or without hwe:
```
 linux-image-generic | 5.15.0.25.27           | jammy            | amd64, arm64, armhf, ppc64el, s390x
 linux-image-generic | 5.15.0.76.74           | jammy-security   | amd64, arm64, armhf, ppc64el, s390x
 linux-image-generic | 5.15.0.76.74           | jammy-updates    | amd64, arm64, armhf, ppc64el, s390x
 linux-image-generic | 5.15.0.79.76           | jammy-proposed   | amd64, arm64, armhf, ppc64el, s390x
 linux-image-generic | 5.15.0.1007.7          | jammy            | riscv64

```
Just have to wait it out.

---

### Post by mylesmorales1940 on 2023-07-14
Thanks for the update and I will wait until the end of the month as suggested.

Thanks for the quick reply.

Myles

---

### Post by guiverc on 2023-07-14
I'll just add that you can see it coming

```

linux-image-generic-hwe-22.04-edge | 6.2.0.25.25~22.04.5   | jammy-proposed   | amd64, arm64, armhf, ppc64el, s390x

```

I'm not sure the *edge* kernel will provide *livepatch* support though (*sorry I don't know, the intention of edge is testing so I'd not use it in production anyway!*).. and the line I provided was one 1fallen missed (*or omitted on purpose sorry*).

---

### Post by akhomenko on 2023-09-04
Despite it being September 4th, I see no evidence of Livepatch HWE kernel stack support being available yet. Am I just completely missing it, or has it been delayed?

---

### Post by guiverc on 2023-09-04
```

 linux-generic-hwe-22.04 | 5.15.0.25.27        | jammy           | amd64, arm64, armhf, ppc64el, s390x
 linux-generic-hwe-22.04 | 6.2.0.32.32~22.04.9 | jammy-security  | amd64, arm64, armhf, ppc64el, s390x
 linux-generic-hwe-22.04 | 6.2.0.32.32~22.04.9 | jammy-proposed  | amd64, arm64, armhf, ppc64el, s390x
 linux-generic-hwe-22.04 | 6.2.0.32.32~22.04.9 | jammy-updates   | amd64, arm64, armhf, ppc64el, s390x

```

Ubuntu 22.04 reached 22.04.3 awhile back ([https://fridge.ubuntu.com/2023/08/11/ubuntu-22-04-3-lts-released/](https://fridge.ubuntu.com/2023/08/11/ubuntu-22-04-3-lts-released/)) which is where it was expected (ie. 6.2 kernel)

I'm not using 22.04 (*jammy*), or a LTS user, thus  aren't a *livepatch* user, but I'd check what you're actually using; are you using HWE?, don't have any *holds*?, have applied all security upgrades? (*full-upgrade*) etc. Have Ubuntu Pro *enabled?*

Maybe helpful - [https://ubuntu.com/security/livepatch/docs/livepatch/how-to/enable](https://ubuntu.com/security/livepatch/docs/livepatch/how-to/enable)

If you need help, I'll suggest you mention what you're now using, as all details in this thread  were 5.19 which isn't a *supported* kernel now.

---

### Post by akhomenko on 2023-09-05
I was referring to it not being listed here [https://ubuntu.com/security/livepatch/docs/livepatch/reference/kernels](https://ubuntu.com/security/livepatch/docs/livepatch/reference/kernels), but it appeared in the last 22 hours since I posted the message :D

---

### Post by mylesmorales1940 on 2023-09-05
Yes I have 22.04.3

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	        22.04
Codename:       jammy

Today the Livepatch icon appeared for the first time since July 23, 2023: 

I clearly have more administration work to do:

SERVICE          ENTITLED  STATUS    DESCRIPTION
anbox-cloud      yes       disabled  Scalable Android in the cloud
cc-eal           yes       n/a       Common Criteria EAL2 Provisioning Packages
esm-apps         yes       enabled   Expanded Security Maintenance for Applications
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
fips             yes       n/a       NIST-certified core packages
fips-updates     yes       n/a       NIST-certified core packages with priority security updates
livepatch        yes       disabled  Current kernel is not supported
realtime-kernel  yes       disabled  Ubuntu kernel with PREEMPT_RT patches integrated
&#9500; generic        yes       disabled  Generic version of the RT kernel (default)
&#9492; intel-iotg     yes       disabled  RT kernel optimized for Intel IOTG platform
ros              yes       n/a       Security Updates for the Robot Operating System
ros-updates      yes       n/a       All Updates for the Robot Operating System
usg              yes       enabled   Security compliance and audit tools


I do have kernel 6.2

uname -r
6.2.0-32-generic

---

