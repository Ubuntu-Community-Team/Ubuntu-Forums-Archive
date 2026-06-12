---
title: "computer hibernates while working"
date: 2009-05-20
forum: General Help
---

### Post by epek on 2009-05-20
My Shuttle SN41G2 (Motherboard FN41) show interesting behaviour since upgrading from 8.10 to 9.04: It simply hibernates itself while I am still working.
Suspend options within the BIOS are turned off. Changing the values within gnome's power settings ("never") does not help. Pressing a key on the (PS/2) keyboard seems to dilate the problem, mouse action on a USB connected mouse does not. Error occurs in between 10 Minutes an 30 Minutes.
The positive thing about it: hibernation itself works perfectly now - only much too often!

Currently I am unable to test any patches, because the BIOS' flash chip seems to have died after resetting to factory defaults while debugging this and boot menu issue. The chip was yet another preprogrammed replacement chip, which I ordered recently. I'll try again as soon as I have retrieved another replacement or until I managed to flash it again.

Still I don't think, that the hibernation problem was not caused by that issue, but by either some strange acpi bug or an error with gnome's power controls or something within the event management combined with the power controls.

Has someone experienced similiar problems so far?

---

### Post by utnubuuser on 2009-05-20
Not a key-combination issue?

Maybe your computer has MONO!!!

---

### Post by epek on 2009-06-03
key-combination:

I don't think so. It happens, when no key is pressed for a while. If I open a terminal and submit a command like e.g. ls, find, ps, the machine won't suspend. Mouse action is ignored.
As long as there is no imaginary "no-key" as a complement key for the "any-key", I cannot imagine what you are thinking of. ;)

Meanwhile, I was able to reproduce the error on another mainboard: gigabyte ga7vtxh. So I believe the problem to be rather software related then hardware related.
Maybe some event hooks are missing in the automatically configured xorg.

Mono: you don't mean the .net implementation on Linux: mono-framework(1,2), do you?

If so the following are installed (dpkg -l | grep mono):
ii  libmono-addins-gui0.2-cil                     0.4-3                                                      GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                         0.4-3                                                      addin framework for extensible CLI applications/li
ii  libmono-cairo1.0-cil                          2.0.1-4                                                    Mono Cairo library
ii  libmono-cairo2.0-cil                          2.0.1-4                                                    Mono Cairo library
ii  libmono-corlib1.0-cil                         2.0.1-4                                                    Mono core library (1.0)
ii  libmono-corlib2.0-cil                         2.0.1-4                                                    Mono core library (2.0)
ii  libmono-data-tds1.0-cil                       2.0.1-4                                                    Mono Data library
ii  libmono-data-tds2.0-cil                       2.0.1-4                                                    Mono Data Library
ii  libmono-data1.0-cil                           2.0.1-4                                                    Mono.Data.* libraries (1.0)
ii  libmono-data2.0-cil                           2.0.1-4                                                    Mono.Data.* libraries (2.0)
ii  libmono-getoptions1.0-cil                     2.0.1-4                                                    Mono.GetOptions library (1.0)
ii  libmono-getoptions2.0-cil                     2.0.1-4                                                    Mono.GetOptions library (2.0)
ii  libmono-posix1.0-cil                          2.0.1-4                                                    Mono.Posix library (1.0)
ii  libmono-posix2.0-cil                          2.0.1-4                                                    Mono.Posix library (2.0)
ii  libmono-security1.0-cil                       2.0.1-4                                                    Mono Security library
ii  libmono-security2.0-cil                       2.0.1-4                                                    Mono Security library
ii  libmono-sharpzip0.84-cil                      2.0.1-4                                                    Mono SharpZipLib library
ii  libmono-sharpzip2.84-cil                      2.0.1-4                                                    Mono SharpZipLib library
ii  libmono-sqlite2.0-cil                         2.0.1-4                                                    Mono Sqlite library
ii  libmono-system-data1.0-cil                    2.0.1-4                                                    Mono System.Data library
ii  libmono-system-data2.0-cil                    2.0.1-4                                                    Mono System.Data Library
ii  libmono-system-web1.0-cil                     2.0.1-4                                                    Mono System.Web library
ii  libmono-system-web2.0-cil                     2.0.1-4                                                    Mono System.Web Library
ii  libmono-system1.0-cil                         2.0.1-4                                                    Mono System libraries (1.0)
ii  libmono-system2.0-cil                         2.0.1-4                                                    Mono System libraries (2.0)
ii  libmono0                                      2.0.1-4                                                    libraries for the Mono JIT
ii  libmono1.0-cil                                2.0.1-4                                                    Mono libraries (1.0)
ii  libmono2.0-cil                                2.0.1-4                                                    Mono libraries (2.0)
ii  mono-2.0-gac                                  2.0.1-4                                                    Mono GAC tool
ii  mono-2.0-runtime                              2.0.1-4                                                    Mono runtime (2.0)
ii  mono-common                                   2.0.1-4                                                    common files for Mono
ii  mono-gac                                      2.0.1-4                                                    Mono GAC tool
ii  mono-jit                                      2.0.1-4                                                    fast CLI JIT/AOT compiler for Mono
ii  mono-runtime                                  2.0.1-4                                                    Mono runtime

I don't think, that this is of relevance in this case.  Could you please be more specific about your idea about this?

[1]: [http://en.wikipedia.org/wiki/Mono_(software](http://en.wikipedia.org/wiki/Mono_(software))
[2]: [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

Thanks

---

### Post by directhex on 2009-06-03
Is your system clock running at a "normal" speed? Does it seem accurate?

---

### Post by epek on 2009-06-04
If you are referring to overclocking, I reply that everything is running at the manufacturers hardware specifications.

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 6
model        : 6
model name    : AMD Athlon(tm) XP 1600+
stepping    : 2
cpu MHz        : 1399.810
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
bogomips    : 2799.62
clflush size    : 32
power management: ts

It do not on any of the two boards use any kind of overclocking. Neither on ram nor on the cpu itself. I also checked the systems' temperatures, which are all within the normal range.

It - really - rather seems to be related to keyboard activity, than anything else.

I even tried the Power Management Inhibit applet, which has no influence on the current system's  (ga7vtxh) behaviour whatsoever.

It's really weird and I wouldn't post in a forum, if I had any clue.

On another board (A7n8x deluxe - nvidia) the error does not occur, but that's another system with an other (clean) installation of jaunty. It has to be software related somehow. I am pretty sure a fresh install will solve the problem, but I am curious if someone else has encountered similiar problems after the update. If that's the case, we should find out and report the problem asap.

---

### Post by directhex on 2009-06-04
> **epek said:**
> If you are referring to overclocking, I reply that everything is running at the manufacturers hardware specifications.

Actually I meant as in "2:16 PM" clock. Is it running normally and accurately?

---

