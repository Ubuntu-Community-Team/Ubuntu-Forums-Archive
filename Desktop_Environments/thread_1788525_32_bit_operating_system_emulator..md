---
title: "32 bit operating system emulator."
date: 2011-06-22
forum: Desktop Environments
---

### Post by davoudi on 2011-06-22
Is there any 32 bit operating system emulator (like a bridge) that I could easily use those packages or software that can be installed on a 32 bit operating system easier? Something easier than emulating another Ubuntu using Virtualbox.

---

### Post by 3Miro on 2011-06-23
You can install 32-bit packages with
```
dpkg --force-architecture -i <package>
```

You will need ia32 libraries to run the installed program.

Out of curiosity, what are those 32-bit packages that you want to install?

---

### Post by davoudi on 2011-06-24
> **3Miro said:**
> You can install 32-bit packages with
```
dpkg --force-architecture -i <package>
```

You will need ia32 libraries to run the installed program.

Out of curiosity, what are those 32-bit packages that you want to install?

I have problem with other software like ROOT (Cern), cisco vpn etc. These software apparently get installed on 32-bit operating system easier than 64. Thanks for help.

---

