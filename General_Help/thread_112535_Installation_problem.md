---
title: "Installation problem"
date: 2006-01-04
forum: General Help
---

### Post by overkordbaever on 2006-01-04
I'm trying to install Kubuntu (5.10) on a hp 509.se but after pressing enter at the first screen (of the install, the screen where I can choose kernel), the computer loads some stuff but then restarts. What can be the problem?

---

### Post by byen on 2006-01-04
ok.. here is what you do...
1.first after downloading the ISO make sure that yu check the integrity of the ISo by using a program like this:
[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)
(free and secure)

2.now...after doing this Go to [www.downloads.com](www.downloads.com) and search for the program "deepburner". its free and was developed by the developers with ISO burning in mind. It is really good and damn easy to use. Download it and burn the cd as an ISO project at a slower speed. Let me know if you have any probs. I might have some alternatives.
PS- some people have better luck by -turning the ACPI feature off at the boot menu.And remember if you have windows or other Operating systems and wanna dual-boot.

---

### Post by gingermark on 2006-01-04
It's highly possible there isn't a problem. Kubuntu copies over a load of files, and then restarts and continues the installation.

You might want to remove the CD, or change the boot order in your BIOS to boot the Kubuntu hard drive first.

Apologies if this isn't what you mean.

---

### Post by overkordbaever on 2006-01-04
[QUOTE=gingermark]It's highly possible there isn't a problem. Kubuntu copies over a load of files, and then restarts and continues the installation.

You might want to remove the CD, or change the boot order in your BIOS to boot the Kubuntu hard drive first.

Apologies if this isn't what you mean.[/QUOTE]

Well, I haven't installed anything of it yet...

---

### Post by overkordbaever on 2006-01-04
Turning off acpi worked. Thank you for the help gingermark.

Anyway, before I posted this thread, I tried booting with linux noacpi and nolacpi (I think it was, doesn't really remember) but it didn't work. After reading gingermark's post, I checked the boot options some more and found acpi=off and that worked.

---

