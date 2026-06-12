---
title: "Breezy hangs during install"
date: 2006-03-19
forum: Desktop Environments
---

### Post by calvinpriest on 2006-03-19
Ok, I've been fiddling with this for days, and tried lots of stuff...

The facts:
- MSI MS-6368 VER2, Via Cyrix III 667, RTL8139, 192MB RAM
- Hangs during install of Breezy, but if I do a "server" install everything is fine until I do "apt-get install ubuntu-desktop". After that it hangs on login.
- Live CDs of Hoary and Dapper Flight 5 boot up fine (haven't tried Breezy Live)
- Installed fine and works with SimplyMepis and Xandros
- Crashes and burns during install with Fedora, PCLinux OS, Dapper Flight 5 (though live CD of Dapper and PCLinux OS work fine)
- After doing a server install of Breezy, I was able to selectively install X and icewm and gdm (and dependencies).  I could get into icewm and surf the internet with Firefox--all was well.
- After installing ubuntu-desktop I can still login in Recovery Mode.  From there I can selectively uninstall packages.  I thought I'd try a process of elimination, but it's time consuming :-(.
- I have tried adding "noapic nolapic acpi=off" to the command line as recommended in some of the threads here.

Any thoughts?

---

### Post by Blairboy on 2006-03-19
I'm sorta having the same problem with my Frankenstein's monster box.  I think it might be overheating the cpu, so I'm going to get some arctic silver today and try it out.  I'll let you know if that's the problem, because I had winxp installed on it, and it kept freezing after a couple of hours of use.

---

### Post by calvinpriest on 2006-03-19
In my case, I think the hardware is fine.  In addition to Xandros and Mepis installing, Win2K installed as well.

---

### Post by calvinpriest on 2006-03-19
To add to the list of things I have tried:
- New hard drive
- Turned off onboard sound, modem & usb in the BIOS & reinstalled

---

