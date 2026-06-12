---
title: "1420N: hardware virtualization disabled in BIOS?"
date: 2007-08-27
forum: Dell  Ubuntu Support
---

### Post by kthakar on 2007-08-27
I tried to install KVM on my shiny new 1420N preinstalled with Ubuntu. Unfortunately, I couldnt do so. I followed instructions as noted on [https://wiki.ubuntu.com/kvm](https://wiki.ubuntu.com/kvm) . When I tried to modprobe kvm-intel, I got the error message 
FATAL: Error inserting kvm_intel (/lib/modules/2.6.20-16-generic/kernel/drivers/kvm/kvm-intel.ko): Operation not supported

dmesg confirmed what the wiki said
"[ 2513.140000] kvm: disabled by bios"

I am rather surprised that hardware virtualization support has been disabled in 1420N. Does anyone know workarounds for this problem?

---

### Post by sciurus on 2007-08-28
I had the surprised realization that it was disabled. The solution is simple: just enable it in the BIOS.

---

### Post by joehill on 2008-05-07
I'm using a new Dell Latitude D830 and "egrep '^flags.*(vmx|svm)' /proc/cpuinfo" tells me my CPU supports virtualization.  But I get the same message (kvm: disabled by bios).

I don't see any option in bios to enable it though.  Could it be that the bios is preventing me from using my CPU's features?  Is there any way around this, or am I stuck?  Thanks.

---

### Post by joehill on 2008-05-07
Never mind, I found the setting under "POST Settings".  Kvm works now.

---

