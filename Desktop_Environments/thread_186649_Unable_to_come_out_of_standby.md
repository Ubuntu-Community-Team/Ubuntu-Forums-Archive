---
title: "Unable to come out of standby"
date: 2006-06-02
forum: Desktop Environments
---

### Post by edm1 on 2006-06-02
I´m able to go into stanby fine but when i try to come out of it it sticks on a blank screen. I have to restart the computer which you can probably imagine is really annoying. What do people reckon the problem might be?

---

### Post by bryanlking on 2006-06-02
A lot of people have problems with settings on suspend/standby/hibernate.

The way I corrected my problems was to edit the file /etc/defaults/acpi-support.  It's fairly well documented.  I suggest you make a backup copy 1st before editing in case you get "lost" in your changes.  Just change one item at a time and test.  That way you can adjust the settings appropriate to your machine and needs.

BK

---

### Post by missmoondog on 2006-06-18
neither standby or hibernate work correctly on any of my 5 machines. my only complaint about ubuntu, so far.

---

### Post by dennis1200 on 2006-06-18
also having the same problem on my toshiba laptop. a total newbie to ubuntu, though i suspect it has something to do with the acpi module (at least on toshibas), since toshset does not work due to a kernel without the acpi module compiled into it or loaded or whatever it needs to be (and despite the very straightforward readme in /usr/share/doc/acpi/acpi-support or something like that, i could not do it). my big problem is is that standby is an absolute essential for my computer! its great, but shutting down is the one big no-no - i might end up spending the next 24 hours turning it on and off, hoping it will recognize the hard drive.... but otherwise works like a charm. the acpi module exists, that much i know. i can adjust lcd brightness already, so i am very confused if the problem is with acpi, toshiba hardware, or ubuntu. help!

---

