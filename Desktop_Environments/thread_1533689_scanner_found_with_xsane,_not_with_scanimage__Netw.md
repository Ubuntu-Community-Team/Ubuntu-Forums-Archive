---
title: "scanner found with xsane, not with scanimage / Network scan"
date: 2010-07-18
forum: Desktop Environments
---

### Post by mveltre on 2010-07-18
hi!

I successfully installed all brother modules and tools to get my DCP-135c printer/scanner device to work. 

Xsane finds the scanner locally, it works. But I also like to share the scanner in the network, using saned. It seems to be required that "scanimage -L" finds the scanner. 

But "scanimage -L" doen't find it. "sane-find-scanner" provides the info "found USB scanner (vendor=0x04f9, product=0x01ce) at libusb:002:003". And Xsane works perfectly. 

Does anybody have an idea what's missing to get the scanner work with "scanimage"?

Thanks!
Markus

---

### Post by mveltre on 2010-07-18
re,

I'm sorry... my fail. I've just did also an update which installed a new kernel. All brscan-packages needed to be re-installed. Now it works :)

Markus

---

