---
title: "Writing to the BIOS?"
date: 2009-04-04
forum: General Help
---

### Post by codeseer on 2009-04-04
Would it be possible to write to, or flash, the BIOS from within Ubuntu, without sudo/root permissions? I know you could create a boot disc/disk (with physical access) or add a Grub entry (with sudo), but I'm wondering if it's possible without sudo/root permissions.

---

### Post by geraldm on 2009-04-05
I think this is more dependent upon the host computer, and any such writing would normally be protected by security procedures enforced by the computer.
After ubuntu has booted, any such change, if possible, would require root
permissions.  If you were to discover a way to do it without root permissions it would certainly be a bug, and worthy of a report.

regards,
Gerald

---

### Post by damis648 on 2009-04-05
I am not at my ubuntu machine right now, but as I recall the user would need write access to /lib/firmware, not possible without root permissions.

---

### Post by codeseer on 2009-04-05
I mainly ask out of concern for protecting against this concept of an attack: [http://www.tomshardware.com/news/bios-virus-rootkit-security-backdoor,7400.html]("http://www.tomshardware.com/news/bios-virus-rootkit-security-backdoor,7400.html")

It's like the CiH (Chernobyl) virus that lead hardware manufactures to create better protection in the late 90s. They make another interesting point; that is if a lesser virus could hide out on the system and wait for root usage, it could then make the infection to the BIOS. Though, from my understanding, when using sudo it only has the ability to execute the command given after it when you also have the time out interval set to 0, as I have. I also assume that keylogging is impossible without root access. So, this attack on an Ubuntu system would be fairly difficult probably? I suppose locking the BIOS would prevent it as well.

---

