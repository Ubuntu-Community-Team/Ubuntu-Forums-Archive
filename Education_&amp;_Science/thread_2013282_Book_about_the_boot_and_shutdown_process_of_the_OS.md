---
title: "Book about the boot and shutdown process of the OS"
date: 2012-06-30
forum: Education &amp; Science
---

### Post by azzamite on 2012-06-30
Hello there

Anyone knows a good book reference that describes the boot and shutdown processes of the OS?

For example, the loader loads an image that initializes some devices and then pass the control to the main kernel, then execute the scripts in init.d and so on... (also the bios takes some part in that process)

And for the shutdown process, stuff like saving the random seed, module unload, wait time for processes before killing them and so on...

The more recent the book the better.

---

### Post by Bachstelze on 2012-07-01
"The OS", what OS?

---

### Post by IWantFroyo on 2012-07-01
You could go in and directly look. :|

Unless you want something for a different system. Please be more specific.

---

### Post by azzamite on 2012-07-01
@Bachstelze and @IWantFroyo

I'm looking for something like [this IBM article]("http://www.ibm.com/developerworks/library/l-linuxboot/index.html") but the size of a book if possible.

For instance one thing that is not mentioned in that article if the fact that Linux adjusts the hour on boot because the BIOS clock is not so accurate (my old box used to hang with 2.6.18 because of that).

I need a book that describes that kind of obscure stuff, and also the shutdown process.

---

### Post by abacustrani on 2012-07-06
Bootstrapping is the full name for the process of bringing a computer system to life and making it ready for use. The name comes from the fact that a computer needs its operating system to be able to do anything, but it must also get the operating system started all on its own, without having any of the services normally provided by the operating system to do so. Hence, it must "pull itself up by its own bootstraps." Booting is short for bootstrapping, and this is the term I'll use.[1]

[1] IBM has traditionally referred to the bootstrapping process as the IPL (initial program load). This term still shows up occasionally in AIX documentation.

The basic boot process is very similar for all Unix systems, although the mechanisms used to accomplish it vary quite a bit from system to system. These mechanisms depend on both the physical hardware and the operating system type (System V or BSD). The boot process can be initiated automatically or manually, and it can begin when the computer is powered on (a cold boot) or as a result of a reboot command from a running system (a warm boot or restart).

The normal Unix boot process has these main phases:

Basic hardware detection (memory, disk, keyboard, mouse, and the like).

Executing the firmware system initialization program (happens automatically).

Locating and running the initial boot program (by the firmware boot program), usually from a predetermined location on disk. This program may perform additional hardware checks prior to loading the kernel.

Locating and starting the Unix kernel (by the first-stage boot program). The kernel image file to execute may be determined automatically or via input to the boot program.

The kernel initializes itself and then performs final, high-level hardware checks, loading device drivers and/or kernel modules as required.

The kernel starts the init process, which in turn starts system processes (daemons) and initializes all active subsystems. When everything is ready, the system begins accepting user logins.

---

