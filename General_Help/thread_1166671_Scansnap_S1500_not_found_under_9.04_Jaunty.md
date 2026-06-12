---
title: "Scansnap S1500 not found under 9.04 Jaunty"
date: 2009-05-22
forum: General Help
---

### Post by edwebdev on 2009-05-22
Hi everyone,

I am having some problems getting a new Fujitsu S1500 scanner to function properly with Ubuntu 9.04. The device works flawlessly when I boot my desktop into Windows Vista, but Ubuntu can't seem to find it when I boot into Jaunty.

I have tried using the scanner from the command line with scanimage -L and scanadf -L (both as myself and as root) as well as with the graphical frontends xsane and gscan2pdf. All four programs report that no usable scanners can be found.

When I run sane-find-scanner at the command line (either as myself or root), it finds the scanner and reports the correct manufacturer and product codes. Furthermore, sane-project.org reports that support for the S1500 through sane-backends v. 1.0.19 (the version I have installed) is "complete."

I have modified /etc/sane.d/fujitsu.conf to include the appropriate manufacturer and product codes:

#scansnap S1500
usb 0×04c5 0×11a2

I have also verified that fujitsu is NOT commented out in /etc/sane.d/dll.conf

I have not been able to find any more information towards resolving this problem on the internet at large or on the SANE projects mailing lists.

I'm not sure what I could do next to try and get this thing to work. Any suggestions or information that you can contribute would be greatly appreciated.

With thanks,
edwebdev

---

### Post by latchkeyed on 2009-06-14
FWIW, upgrading the sane packages from karmic koala fixes this. I just installed them and my ScanSnap 1500M came up in xsane and gscan2pdf.

---

### Post by almightybunghole on 2009-09-01
Hi,

I have the same scanner connected to a machine running Hardy - could the same fix mentioned above (i.e. installing the sane modules for karmic) work on that too?

Thanks.

AB

---

