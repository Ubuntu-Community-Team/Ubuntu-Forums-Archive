---
title: "Changing Computer"
date: 2016-07-07
forum: Desktop Environments
---

### Post by Geoff_Lane on 2016-07-07
Folks,

Was running 12.04 LTS for some time on my HP laptop with dual core AMD processor.

Laptop failed so put HD in external USB3 enclosure.

Bought new Toshiba 64 bit with quad core AMD A8 processor. 

Only had it a couple of days, seems to boot my Ubuntu 12.04 fine but curious: pmon only shows ONE processor whereas on my old HP it displayed both processor info.

Any ideas why this might be? I have done apt-get update upgrade etc.


Geffers

---

### Post by uNoubu8a on 2016-07-07
Hi,

A similar issue can be found here - [http://ubuntuforums.org/showthread.php?t=2243272](http://ubuntuforums.org/showthread.php?t=2243272)

It may very well be the external HDD enclosure you are using.  Now the reason that attaching a USB device would make one loose the functionality of CPU cores I don't understand >.<



Cheers
404

edit - Perhaps using a newer kernel will solve the issue... if this is the issue you are facing.

---

### Post by Geoff_Lane on 2016-07-10
Strangely I replied outlining some minor graphic problems but the post has disappeared.

Sysmon shows all 4 processors (load) but pmon only reports TEMP on one.

Geffers

---

### Post by uNoubu8a on 2016-07-11
Odd... you could look into the answer to this thread - [https://askubuntu.com/questions/127815/using-quad-core-but-only-1-cpu-entry-in-proc-cpuinfo-is-smp-running-on-my-c](https://askubuntu.com/questions/127815/using-quad-core-but-only-1-cpu-entry-in-proc-cpuinfo-is-smp-running-on-my-c) - about ensuring ACPI features in BIOS is enabled... seems it can also cause this.

---

### Post by ka55o5 on 2016-07-14
> **Geoff_Lane said:**
> Bought new Toshiba 64 bit with quad core AMD A8 processor.
Perhaps now is the time to move on to teh new(est) LTS, 16.04 and leave all those problems behind?..:)

P.S. 
Btw., in the linked threads /askubuntu, how crazy is it that some people had not configured ACPI (from BIOS); Jeeh-sus. =)

**Edit**: Sorz (!), had to edit... Upgrading the system, on a WD system drive (the [first one]("http://paste.ubuntu.com/19382673/")), took FOREVER - and there were many errors, which had to be fixed to get a functional system; so, it's not something that I could recommend - yeah, even though I had just typed it, heh. xD

---

### Post by Geoff_Lane on 2016-07-17
Will do an upgrade at some point but new computer with Win10 (not used yet) and running old OS on external enclosure to safeguard warranty.

Seems all 4 processors working but just one temperature sensor.

Thanks for pointers.

Geffers

---

