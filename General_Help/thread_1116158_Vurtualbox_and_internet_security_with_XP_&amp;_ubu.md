---
title: "Vurtualbox and internet security with XP &amp; ubuntu"
date: 2009-04-04
forum: General Help
---

### Post by metasolaris on 2009-04-04
Hi

Running Intrepid in VirtualBox in XP.

How secure is XP? Can malware which might enter ubuntu while surfing  effect XP?

Does ubuntu exist only in ram?

Thanks

---

### Post by ukblacknight on 2009-04-04
> **metasolaris said:**
> Hi

Running Intrepid in VirtualBox in XP.

How secure is XP? Can malware which might enter ubuntu while surfing  effect XP?

Does ubuntu exist only in ram?

Thanks

XP is as secure as you make it.  Make sure you install the latest updates from Microsoft, keep your anti-virus up to date, don't visit dodgy sites and you should be fine.

Whatever you do in Ubuntu (guest) will not effect XP (host): one reason is that malware is designed to run on Windows systems and not Linux systems, but also the virtualisation layer generally means bad stuff cannot move between the two.  The only way I could think that this could happen if you have sharing folders set up between the guest and the host.

The Ubuntu guest is stored in a virtual drive image, which basically pretends to be a hard drive.  When you start the guest, it loads it into memory (however much you specified whilst setting up the VM).

Hope this helps.

---

### Post by metasolaris on 2009-04-05
Thanks

What happens to your evidence of surfing - the stuff that normally gets written to your hard drive?

(assuming you are browsing with ubuntu-guest)

---

