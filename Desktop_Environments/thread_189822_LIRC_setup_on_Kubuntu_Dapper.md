---
title: "LIRC setup on Kubuntu Dapper"
date: 2006-06-05
forum: Desktop Environments
---

### Post by _Petya_ on 2006-06-05
Hi!

I'm trying to set up LIRC on my Dapper, with homebrew receiver. 
I get this error message when I try to insert lirc_serial module:

# modprobe lirc_serial
FATAL: Error inserting lirc_serial (/lib/modules/2.6.15-23-386/misc/lirc_serial.ko): Unknown symbol in module, or unknown parameter (see dmesg)
# dmesg | tail -n 1
[4322908.982000] lirc_serial: Unknown symbol verify_area

What is the problem?

Petya

---

