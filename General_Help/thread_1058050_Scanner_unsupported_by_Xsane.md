---
title: "Scanner unsupported by Xsane"
date: 2009-02-02
forum: General Help
---

### Post by tempus on 2009-02-02
I like ubuntu a lot and would like it even more if I could find a program that supports my scanner, HPG4050 Scanjet. So far the only program I see that is popular is Xsane and it won't work with my scanner. A look at the list of supported scanners on the xsane website shows mine unsupported. What should I do about this? Or just wait until xsane is updated.

---

### Post by cariboo on 2009-02-02
Have you had a look at this [page]("http://www.sane-project.org/contrib.html"), and sent in the details of the scanner as they have asked. If they get enough details they may create a driver for your scanner.

Jim

---

### Post by OrangeCrate on 2009-02-02
> **tempus said:**
> I like ubuntu a lot and would like it even more if I could find a program that supports my scanner, HPG4050 Scanjet. So far the only program I see that is popular is Xsane and it won't work with my scanner. A look at the list of supported scanners on the xsane website shows mine unsupported. What should I do about this? Or just wait until xsane is updated.

I'm not an expert on XSane, but I'll try to help...

In Intrepid, it should have just picked up on the scanner. HP products are well supported on Linux.

If you're using Hardy, or just want to try this, install the "hpoj" package from Synaptic. It will then run you through a wizard with some simple questions, and hopefully it will detect your scanner.

(That's what I had to do to get my HP Officejet J4550 All-in-One to work on Hardy. The printer was fine, the scanner was problematic, until I installed that package.)

When I updated to Intrepid, it now has something called "hplip", and I uninstalled the hpoj package. It seemed to be conflicting, and once removed, it's working fine now.

Like I said, I'm not an expert on this, and I hope my comments make some sense to you.

---

