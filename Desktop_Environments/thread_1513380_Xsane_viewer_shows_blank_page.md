---
title: "Xsane viewer shows blank page"
date: 2010-06-19
forum: Desktop Environments
---

### Post by gypaete09 on 2010-06-19
I don't know if it only happens under Lucid AMD64, but Xsane suddenly would only show a white page with a even whiter vertical bar in the middle, after scanning from my networked HP 3055 on the local Ethernet.

I tried a lot of things, including deinstalling / reinstalling HPLIP, SANE, XSANE, the whole lot, using synaptic's "complete de-install including configs" option.

After reinstall, Xsane ran into problems finding the scanner via the LAN and I solved that reading this post: [http://ubuntuforums.org/showthread.php?t=1313978](http://ubuntuforums.org/showthread.php?t=1313978)
just to create the UI's for the 3 devices in the printer (printer,fax, scanner)

And it worked again - but only once.
I then tried to change the option in Xsane's scan window to save directly to a file rather than go via the viewer, and the scanned image appeared correctly as saved pdf file.

I flipped back to the viewer option, because I *need* to check what I scan, and have no other choice for a viewer in xsane.

Result: it worked again, and remained stable. Seems the whole reinstall was useless.

..if it can save someone the whole HPLIP / CUPS / SANE / XSANE reinstall job - maybe, try my last operation first.

):P

---

