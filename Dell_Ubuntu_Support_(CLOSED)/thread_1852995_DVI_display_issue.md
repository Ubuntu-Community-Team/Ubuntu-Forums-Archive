---
title: "DVI display issue"
date: 2011-10-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shahansudu on 2011-10-01
Hi,
 I have a Dell latitude E6500 and that comes with a VGA out. I also have a DVI KVM switch so I needed to connect my laptop to the KVM. Bought a VGA-to-DVI convertor and plugged into the KVM. My keyboard and mouse works fine and the other machine connected to KVM works fine so I know the KVM switch is ok. What I suspect is that I probably dont have the correct driver to make this happen. Following is what I get from lspci

```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

How do I get the my machine to detect the DVI monitor? or what should I install to make this happen? Thank you in advance

---

### Post by shahansudu on 2011-10-02
Solved the issue by using the display port instead of the VGA...

---

