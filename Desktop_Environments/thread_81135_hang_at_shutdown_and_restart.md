---
title: "hang at shutdown and restart"
date: 2005-10-23
forum: Desktop Environments
---

### Post by hunteramor on 2005-10-23
I've been unable to successfully shutdown or restart since upgrading to Breezy.  When I try, the system hangs after the following message:

[INDENT]
* Deactivating swap...
unmount: tmpfs busy - remounted read only
[RIGHT][ok][/RIGHT]

* unmounting local file systems...
unmount: tmpfs busy - remounted read only[/INDENT]

does anyone know why i might be encountering this problem?  thanks, I appreciate the help.

---

### Post by hunteramor on 2005-10-25
little bump...  sorry - i can't figure this out and i'd appreciate any help!

---

### Post by ecobuntu on 2005-10-26
[QUOTE=hunteramor]I've been unable to successfully shutdown or restart since upgrading to Breezy.  When I try, the system hangs after the following message:

[INDENT]
* Deactivating swap...
unmount: tmpfs busy - remounted read only
[RIGHT][ok][/RIGHT]

* unmounting local file systems...
unmount: tmpfs busy - remounted read only[/INDENT]

does anyone know why i might be encountering this problem?  thanks, I appreciate the help.[/QUOTE]

see this
[https://bugzilla.ubuntu.com/show_bug.cgi?id=18163](https://bugzilla.ubuntu.com/show_bug.cgi?id=18163)
I think you're experiencing the same thing.  Add to the bug report

---

### Post by hunteramor on 2005-10-26
it appears i was wrong on one point - it's not at shutdown, only restart.

i don't think it's the same bug since i get beyond hitting the restart button, there's maybe a page of system messages before i get the one i hang on.  i'll leave a comment on the bug anyway.

thanks for the help.

---

### Post by tylerD on 2005-11-10
I am having the same problem.  It's only on restart.  I get the same info as above and the rest below then it hangs.

*Shutting down LVM Volume groups...[ok]
*Rebooting...
[4386032.520000] Restarting system.


Any help would be greatly appreciated.

Thanks.

---

### Post by hunteramor on 2005-11-10
glad i'm not the only one  =)

---

### Post by tylerD on 2005-11-14
What hardware are you running?  I'm using a Dell optiplex system using the Intel 915g chipset.

---

### Post by limewolf on 2005-11-24
[QUOTE=tylerD]I am having the same problem.  It's only on restart.  I get the same info as above and the rest below then it hangs.

*Shutting down LVM Volume groups...[ok]
*Rebooting...
[4386032.520000] Restarting system.

[/QUOTE]

I have exactly the same problem as you, but I've been unable to solve it so far. I'm going to keep trying to sort it out in anycase...

---

### Post by souki on 2005-11-24
do you have an ipw2100 wireless card?
look at this thread [http://ubuntuforums.org/showthread.php?t=75314&page=5](http://ubuntuforums.org/showthread.php?t=75314&page=5)

---

### Post by limewolf on 2005-11-25
[QUOTE=souki]do you have an ipw2100 wireless card?
look at this thread [http://ubuntuforums.org/showthread.php?t=75314&page=5](http://ubuntuforums.org/showthread.php?t=75314&page=5)[/QUOTE]


I don't have a wirless card in the machine. It's odd that it worked ok in hoary - I've not altered the hardware, so I guess it's probably a software issue (or maybe a newer driver is exposing a hardware problem) - so far I'm no nearer to woking it out or fixing it.

---

### Post by devnet on 2006-05-11
I'm hitting this after ACPI Kicks in on an IBM Netvista with a bare install (Server).  

I think it is ACPI conflicts that are giving us this error.  After reboot, I have no problems.  Try disabling ACPI at BIOS and see what happens.

I'm going to attempt this as well and see if things are good.

---

