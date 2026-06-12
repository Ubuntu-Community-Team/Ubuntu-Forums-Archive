---
title: "Inspiron 6000 - can't install anything?"
date: 2010-12-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by AKADriver on 2010-12-12
I've tried 10.10 and 10.04. The 10.04 install gets further, but not by much. In both cases I'm attempting to install from a live CD.

Using 10.10, the installer seems to proceed normally for a while, then just halts at the screen with the ubuntu logo and series of dots. Using the text-only installer and choosing any of the options like acpi=off (which I needed for my Inspiron 26xx) or nomodeset (which I'd seen recommended for the Inspiron 600m) caused the install to fail with a kernel panic.

Using 10.04, no matter which options I choose, the install runs for a while then eventually drops me to a screen showing only:

(process:297): GLib-WARNING **: getpwid_r(): failed due to unknown user id (0)

Something seems to still be running here, because if I tap the power button it ejects the disc... and the bluetooth indicator is blinking.

Okay, I've now tried installing 10.10 from a USB drive, and it's working! Interesting. I don't know what was causing problems with the CDs. The 10.10 CD I was using successfully installed on my desktop last week.

Edit 2: never mind, now that the install has finished, the wireless works too.

:D

---

### Post by doronk on 2011-01-09
which ubuntu revision did you use for the inspiron 6000, desktop or netbook? any tips for a novice?

---

