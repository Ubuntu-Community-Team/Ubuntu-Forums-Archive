---
title: "New install went wrong"
date: 2016-08-22
forum: Debian
---

### Post by Omar_Jair on 2016-08-22
So i had Lubuntu on this old machine, so i decided to change to Debian 8, everything in the installation went good except for the ending everytime i try to boot i get directed to the grub command prompt, it says lie
Minimal BASH-like editing is supported. TAB lists possible command completions.
grub>

so i type "exit" and then i get this
[ATTACH=CONFIG]270810[/ATTACH]
any ideas on how to boot normally like any human would do?

---

### Post by oldfred on 2016-08-22
Moved to Debian forum.

That is the UEFI boot menu.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Omar_Jair on 2016-08-22
Is it safe to install this on Debian?

---

### Post by oldfred on 2016-08-22
I do not see why not.
But just run Summary Report, do not try any auto fixes until someone has reviewed it.

---

### Post by Omar_Jair on 2016-08-22
Sadly this is one of the cases where it turns out to go wrong, boot repair did nothing but add another OS boot manager being the windows one this time, at this poind i dont know if wiping the entire disk with gparted and then install debian is viable

---

### Post by arochester on 2016-08-25
> this old machine Does this old machine have a MAKE and MODEL? Or can you tell us some basic specs? How much RAM have you got?

What installation method did you use? (Where did you get it from?)

If the machine is so old I don't understand why you should be doing a UEFI installation. Have you tried turning off UEFI in the BIOS and going for Legacy instead?

---

### Post by Omar_Jair on 2016-09-21
Finally solved it by using the boot-repair program. (quite late i see)

---

