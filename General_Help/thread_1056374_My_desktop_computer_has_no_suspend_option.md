---
title: "My desktop computer has no suspend option?"
date: 2009-01-31
forum: General Help
---

### Post by riskbreaker927 on 2009-01-31
Like, literally - every place that normally gives me an option to suspend my computer currently does not.

I recently built this desktop using this motherboard:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500004](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500004)

and I currently have no way of suspending my machine. Hibernation is listed but I don't want that and won't bother trying it because I installed without a swap partition. Anyone know what the problem is?

---

### Post by riskbreaker927 on 2009-01-31
As an aside, if I run powertop, where it normally tells me how many watts i'm using at the moment, it currently only returns "no ACPI power usage estimate available."

I feel like something is configured wrong on my system, but I have no idea what. Any ideas?

---

### Post by tom66 on 2009-01-31
Linux's suspend at the moment is quite... glitchy. It's not perfect, and doesn't work on all machines. Do you know if suspend works in other operating systems, e.g. Windows?

---

### Post by riskbreaker927 on 2009-01-31
I'm aware of how glitchy suspend is - I've been running Ubuntu for years now on an Inspiron 1501, thank god I've moved onto an Inspiron mini which does it perfectly - and I could deal with glitchy suspend. My problem is I don't even have anything to click on to try it.

I haven't tried Windows XP on this machine yet, although it was on the to do list, so I'll get back to you.

---

### Post by riskbreaker927 on 2009-01-31
One more thing. "cat /proc/acpi/sleep" returns:

```

S0 S1 S4 S5 

```

I notice S3 is missing... does that mean my hardware doesn't support it?

---

### Post by riskbreaker927 on 2009-02-01
Any ideas...?

---

### Post by robobot on 2009-02-01
Regarding the missing S3, check your BIOS. There's usually an option that lets you select whether you want to use S1 or S3 for standby. On my system, I have S3 selected, and S1 doesn't show up in /proc/acpi/sleep.

---

### Post by riskbreaker927 on 2009-02-01
Good form lad, that was just the thing I needed to do.

You can close this thread, problem solved.

---

