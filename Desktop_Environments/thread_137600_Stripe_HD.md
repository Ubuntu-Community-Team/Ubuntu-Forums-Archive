---
title: "Stripe HD"
date: 2006-02-28
forum: Desktop Environments
---

### Post by jwe on 2006-02-28
Hi

Can you stipe two hard drives in Linux?

---

### Post by sprucio on 2006-02-28
Yes.

mdadm and mdadm-tools are what you'll need.

---

### Post by jwe on 2006-02-28
Thanks,
I just had a browse on Google and can only see mirroring so far.
Can you stipe two IDE drives that is not identical in size?

---

### Post by jwe on 2006-02-28
OK duh, found it.

---

### Post by sprucio on 2006-02-28
You can stripe two drives that are not the same size but for optimal performance, it's better that you use the exact same drive (vendor, space, model).

Regarding space, it will always default to the smaller hard drive space x <number of drives you have>.

So if you have one hd that's 20GB and one that's 40GB, the maximum you'll get with the stripe will be 40GB.

Also, keep in mind that hardware RAID with an dedicated card (PCI) is often a better solution if costs is not an issue since will not rely on the CPU and memory (the card itself has it's own CPU and memory).

---

