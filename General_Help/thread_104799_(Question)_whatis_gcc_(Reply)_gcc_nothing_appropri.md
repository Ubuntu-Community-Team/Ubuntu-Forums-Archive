---
title: "(Question) whatis gcc (Reply) gcc: nothing appropriate"
date: 2005-12-16
forum: General Help
---

### Post by AlexanRO on 2005-12-16
I am trying to install klamav using the klamav-0.32-installer, the INSTALL documentation is pretty straight forward (I lied) it states the following:

==========================
Installation Instructions:
==========================

Do what the filename tells you!!

(e.g. sh ./DoubleClickOrExecuteMeToInstallKlamaAV-0.XX
	or ./DoubleClickOrExecuteMeToInstallKlamaAV-0.XX)

Any problems with the install please mail: [email]klamav-users@lists.sourceforge.net[/email].

How is that for straight forward?!  Anywho, I "Do what the filename tells you!!" as instructed above only I receive the following error:

***** Dazuko
***** Running configure (./configure)...
checking host system type... Linux
checking for make utility... ok (make)
checking for C compiler... none found
error: no C compiler found on this system
***** Return value 1

What no compiler? that was my reaction so I synaptic gcc it installs gcc-4.0 and gcc-4.0-base at least I was under the guise that it did.  Feeling suspicious I open the console and type:

```
whereis gcc
```

it renders the following output:

```
gcc: /usr/lib/gcc
```

Okay so now I am really curious so I type:

```
whatis gcc
```

ironically it renders:

```
gcc: nothing appropriate.
```

When I saw this initially all I could do is laugh --but I assure you this is no laughing matter....

what do I need to do to fix this?

TIA

AlexanRO

---

### Post by matthew on 2005-12-16
sudo apt-get install build-essential

then try again

---

### Post by AlexanRO on 2005-12-17
[QUOTE=matthew]sudo apt-get install build-essential

then try again[/QUOTE]

Awesome! Thank you, what you suggested solved the compiler error; however, now I get the following:

***** Dazuko
***** Running configure (./configure)...
checking host system type... Linux
checking for make utility... ok (make)
checking for C compiler... ok (cc)
kernel source in /lib/modules/2.6.12-1-386/build... no
kernel source in /usr/src/linux... no
error: kernel source files not found
***** Return value 1


The kernel-source for the kernel I am using was not available when I checked Synaptic, can I locate the package elsewhere?

---

