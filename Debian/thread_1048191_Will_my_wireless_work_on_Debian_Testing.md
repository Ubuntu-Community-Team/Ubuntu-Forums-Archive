---
title: "Will my wireless work on Debian Testing?"
date: 2009-01-23
forum: Debian
---

### Post by Hallvor on 2009-01-23
I have a spare computer that I am thinking of installing Debian testing (Lenny) on. It is a P3(?) 1,5 GHZ Dell Optiplex with 512 MB RAM. I am thinking of buying a Ralink rt2500 wireless pci for it, but I am not sure of it will work with Debian out of the box.

Does anyone here know if the Ralink rt2500 will work with Debian without too much hassle? Preferably out of the box.

---

### Post by markharding557 on 2009-01-23
i believe this chip is well suppoted in linux so it should work

---

### Post by Bachstelze on 2009-01-24
What he said.

---

### Post by polmir on 2009-01-26
[http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto]("http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto")

---

### Post by wolfen69 on 2009-01-27
> **polmir said:**
> [http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto]("http://rt2x00.serialmonkey.com/wiki/index.php/Debian_rt2500_Howto")

i have a rt2500 wireless chipset. the driver is in the repos when you have the non-free repos enabled.

---

### Post by odiseo77 on 2009-01-29
This card works perfectly for me, but although the kernel has support for it, it doesn't work fine out of the box in the default kernel (not in my case, at least). The solution is pretty simple: before installing the beta driver source as explained in the wiki linked above, remove the rt2500pci rt2x00pci and rt2x00lib modules from the kernel (***modprobe -r <module_name>***), and blacklist them in "/etc/modprobe.d/blacklist" (add "blacklist <module_name>" for each one of these modules).

Greetings.

---

