---
title: "Current kernel not supported livepatch"
date: 2023-05-14
forum: Desktop Environments
---

### Post by AnupamMitra on 2023-05-14
My desktop environment is Ubuntu 22.04 64 bit. However, when I entered *ua status* it shows -
```

ua status 
SERVICE          ENTITLED  STATUS    DESCRIPTION
esm-apps         yes       enabled Expanded Security Maintenance for Applications
esm-infra         yes       enabled Expanded Security Maintenance for Infrastructure
livepatch          yes       warning Current kernel is not supported
realtime-kernel yes       disabled Ubuntu kernel with PREEMPT_RT patches integrated
usg                  yes       disabled Security compliance and audit tools

NOTICES
The current kernel (5.19.0-41-generic, amd64) is not supported by livepatch.
Supported kernels are listed here: https://ubuntu.com/security/livepatch/docs/kernels

```

How to fix the issue?

---

### Post by deadflowr on 2023-05-14
Either dropback to the GA kernel, or way until the HWE kernel reaches it's [s]final[/s] next version when [s]24.04.2[/s] 22.04.3 comes out.
Current kernel supported is the 5.15 series, also known as the GA kernel.
In time they will add the HWE kernel when it reaches it's [s]final[/s] next version, [s]whatever the version used in 24.04.[/s]
[s]This is how they have done it in the past.[/s]

Edit: I see they are now going to start supporting livepatch for HWE kernels before the final version is reached starting with 6.2 which should becoming to 22.04 in the next few months.
See: [https://ubuntu.com/blog/canonical-livepatch-gets-even-better-now-supporting-hardware-enablement-kernels]("https://ubuntu.com/blog/canonical-livepatch-gets-even-better-now-supporting-hardware-enablement-kernels")
And a probably easier read on it here: [https://www.omgubuntu.co.uk/2023/04/ubuntu-livepatch-hwe-kernels]("https://www.omgubuntu.co.uk/2023/04/ubuntu-livepatch-hwe-kernels")

---

### Post by AnupamMitra on 2023-05-18
> **deadflowr said:**
> Either dropback to the GA kernel, or way until the HWE kernel reaches it's [s]final[/s] next version when [s]24.04.2[/s] 22.04.3 comes out.
Current kernel supported is the 5.15 series, also known as the GA kernel.
In time they will add the HWE kernel when it reaches it's [s]final[/s] next version, [s]whatever the version used in 24.04.[/s]
[s]This is how they have done it in the past.[/s]

Edit: I see they are now going to start supporting livepatch for HWE kernels before the final version is reached starting with 6.2 which should becoming to 22.04 in the next few months.
See: [https://ubuntu.com/blog/canonical-livepatch-gets-even-better-now-supporting-hardware-enablement-kernels](https://ubuntu.com/blog/canonical-livepatch-gets-even-better-now-supporting-hardware-enablement-kernels)
And a probably easier read on it here: [https://www.omgubuntu.co.uk/2023/04/ubuntu-livepatch-hwe-kernels](https://www.omgubuntu.co.uk/2023/04/ubuntu-livepatch-hwe-kernels)

Thanks deadflowr.  Due to my indisposition, I couldn't reply in time. As I understood from the given links, I have to wait another 3/4 months. Alright. 

Thanks once again for guiding me like many other occasions earlier.

---

### Post by Paddy Landau on 2023-05-20
I saw this on my machine as well.

Does this mean that if you want to use Livepatch, you should never allow the kernel to update until you see the new version on the [list of supported kernels]("https://ubuntu.com/security/livepatch/docs/livepatch/reference/kernels")?

---

### Post by idmbe on 2023-05-21
Same here, after regular update since weeks ago, that mean need roll back to 5.15 (for desktop), but on server still on 5.15 after regular update & upgrade and work well.
I guess (Pro service & live patch) more benefit on server than desktop.

---

### Post by ajbozdar on 2023-05-23
I just saw this warning on my terminal. Your reply was helpful.

Thank you.

---

