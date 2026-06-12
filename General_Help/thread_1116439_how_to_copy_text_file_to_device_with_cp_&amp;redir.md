---
title: "how to copy text file to device with cp &amp;redirection"
date: 2009-04-04
forum: General Help
---

### Post by mark bower on 2009-04-04
i have set up a virtual com port enroute to talking to a printer via bluetooth.  the code below(substituting my text file) was posted as working, but does not work for me (althoh the dongle light comes on).  what syntax am i missing?

_code_
$ls BTtest.txt >/dev/rfcomm0

_response_
cp: missing destination file operand after BTtest.txt

if all works right, the file BTtest.txt should transmit to a BlueTake BT-200 attached to my HP printer, and the file should be printed at the printer.

---

### Post by lloyd_b on 2009-04-04
> **mark bower said:**
> i have set up a virtual com port enroute to talking to a printer via bluetooth.  the code below(substituting my text file) was posted as working, but does not work for me (althoh the dongle light comes on).  what syntax am i missing?

_code_
$**ls** BTtest.txt >/dev/rfcomm0

_response_
cp: missing destination file operand after BTtest.txt

if all works right, the file BTtest.txt should transmit to a BlueTake BT-200 attached to my HP printer, and the file should be printed at the printer.

"ls"?  Did you mean "cp"?  At any rate, "cp" is the wrong tool - what you want to use is "cat":```
cat BTtest.txt > /dev/rfcomm0
``` should dump the contents of "BTtest.txt" into the device "/dev/rfcomm0".

Lloyd B.

---

### Post by mark bower on 2009-04-04
yes (you were correct), cp not ls 

o.k., i tried cat and two good things: 1) the blue light on the dongle flickers for a while indicating a transmission and 2) no error msg.  so cat looks like a move in the right direction.  i thought i had it made.

but, nothing arrives at the BT-200 (no blue to red light indicator change).  i have verified that the dongle sees the BT-200 using $sdptool search sp [MAC address of BT-200].  also, using "setup device" at bluetooth icon on the tool bar the BT-200 is seen,however, i get the pairing failed msg.  so probably my hopes for a command line work around are no good.  any other ideas?

mark b

---

