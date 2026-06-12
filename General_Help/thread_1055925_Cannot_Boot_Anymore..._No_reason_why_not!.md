---
title: "Cannot Boot Anymore... No reason why not!"
date: 2009-01-31
forum: General Help
---

### Post by DrMelon on 2009-01-31
Hey there everyone!

Here's my situation;
I run Ubuntu as a dual boot with Windows XP. All so fine, so good! It worked perfectly for ages, but I stopped using Ubuntu for about 3 months (as I had found some games that wouldn't work on wine and I really love playing them). So, when I decided to boot up in Ubuntu, I found that it wouldn't start...

What happens is this: I watch the little progress bar. It moves a little bit up, and then stops there forever.

Ah well, I thought, I'll just start in recovery and see what's up.

So when I do, boot goes as normal until this bit appears:
```
ACPI: PCI Interrupt 0000:00:0e:0 [A] -> GSI 17 (level, low) -> IRQ 18
```

After this line, boot stops and will not continue.
After much figuring stuff out, I found that the PCI card in question is my Ethernet NIC. Yet I know it works perfectly well, since I've just written this post to you through it.

I can't work out how to fix it or bypass it; because "acpi=off" just doesn't display the messge (yet it still hangs round there) and "pci=noacpi" doesn't do diddly-squat.

This is really irritating me, because I can't boot into my beloved Ubuntu, and apparently for no reason other than I didn't use it for a while.

---

### Post by 73ckn797 on 2009-01-31
Have you made any BIOS changes in the period since last using Ubuntu?

---

### Post by DrMelon on 2009-01-31
No, I haven't. Which is even stranger: I could understand Ubuntu's confusion if I had changed anything.

---

### Post by DrMelon on 2009-02-01
Help... anybody?

:(

---

### Post by dexter on 2009-02-01
Can you still boot with a live cd?

---

### Post by DrMelon on 2009-02-01
Yes, I can still boot with the Ubuntu Live CD.

---

### Post by DrMelon on 2009-02-01
Am I going to have to reinstall Ubuntu? :(

---

### Post by The Cog on 2009-02-01
It's not something I would know how to fix without reinstalling.

If you do decide to reinstall, probably the easiest way is to use gparted on the live CD to delete the existing Linux partitions, then you can just let the installer use the available free space. Otherwise, you would probably have to go for manual partitioning.

---

### Post by DrMelon on 2009-02-02
Ok, that's a good idea. Goodbye, my faithful old Ubuntu hound...

---

