---
title: "Cannot Set proper resolution 17inch LCD"
date: 2008-10-31
forum: Desktop Environments
---

### Post by Wiebelhaus on 2008-10-31
Cannot Set proper resolution (1280x1024) on 17inch LCD running on a GF8500 PCI-E with a gig of ram in 8.10 I get a funky 1360x768 as the highest.

I've tried all suggestions I can find as well as the old reliables that unfortunately don't work or are not there anymore.

Screenies attached , any suggestions?

Thanks.

---

### Post by n3hima on 2008-10-31
Try hitting Alt+F2 and running "gksudo displayconfig-gtk", then try selecting a different model of monitor.

---

### Post by Wiebelhaus on 2008-10-31
> **n3hima said:**
> Try hitting Alt+F2 and running "gksudo displayconfig-gtk", then try selecting a different model of monitor.

They Ripped displayconfig-gtk out for some unknown reason.

Thanks for trying mate.

---

### Post by n3hima on 2008-10-31
> **sx66gns said:**
> They Ripped displayconfig-gtk out for some unknown reason.

Thanks for trying mate.
Whaat!? I wasn't going to be able to upgrade until monday anyway, now I'm reconsididering upgrading at all.

---

### Post by Wiebelhaus on 2008-11-01
Yea man , I don't know - I've been at this a long time and I'm baffled.

---

### Post by azunder on 2008-11-01
I'm having a similar problem with my [monitor]("http://www.tekheads.co.uk/s/product?product=608298&gclid=CPDrgL2x1JYCFQXK1Aod-zVm2w"). I can get the resolution sorted fine via xorg.conf but doing so seems to disable my hardware drivers, enabling the hardware drivers just messes up the resolution again.

And nvidia thinks my monitor is CRT too.

---

### Post by mdurkin on 2008-11-01
me also - exact same symptoms. very frustrating. None of the current range of nvidia fixes on the forum work for me.

---

### Post by Wiebelhaus on 2008-11-10
No ideas?

---

