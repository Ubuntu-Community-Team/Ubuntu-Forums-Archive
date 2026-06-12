---
title: "IBM Thinkpad install issue"
date: 2005-12-20
forum: General Help
---

### Post by BTodd on 2005-12-20
Help! When trying to install from the install CD to an IBM Thinkpad (2611-411) The installation gets hung on the "Linux ATAPI CD-ROM" prompt. Any Ideas??

---

### Post by rcerreto on 2005-12-20
You could find something useful here:

[http://www.linux-thinkpad.org/]("http://www.linux-thinkpad.org/")

---

### Post by BathroomNinja on 2005-12-20
OK, via another thread here in the forums.  Try the following:

When you pop in the CD and get to the screen with the Ubuntu logo, press F2.  Then enter the following:
```

linux pci=noacpi 
```

then press ENTER.

if that doesn't work, reboot, but this time, type in:
```

linux acpi=off noapic nolapic

```

One of those should work.


Special thanks to the Search feature and [This thread]("http://ubuntuforums.org/showthread.php?t=76482")

---

### Post by Benchrest on 2005-12-20
linux acpi=off noapic nolapic. That worked for me. I was pulling my hair out. Problem was I had forgotten what fixed mine. I need to write that down so I have it for Dapper Drake.

---

