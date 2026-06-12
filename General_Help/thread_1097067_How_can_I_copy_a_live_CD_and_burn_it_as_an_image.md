---
title: "How can I copy a live CD and burn it as an image?"
date: 2009-03-15
forum: General Help
---

### Post by alexeix on 2009-03-15
Hi,

I want to create an image from an OS CD/DVD, so I have a backup copy (I own the software and have the registration key).

How can I do this?

I can see that Brasero will allow me to burn an image, but how do I create the image file on my PC, from the original disc?
Thanks.

---

### Post by lisati on 2009-03-15
My choice of tool would be Nero. I haven't used the Linux version yet but the Windows versions I've used have disk copy options. A quick check of the "add/remove programs list tells me that "Gnome CD Master" has a "cd to cd copy" option

---

### Post by flugh on 2009-03-15
In the past, I have used (pseudo device names, not sure what they are these days)

dd if=/dev/cdrom of=mybackup.iso

from the commandline. Then you can burn the .iso with your program of choice (gnome toaster comes to mind, maybe gcombust, just getting refamiliarized with my Ubuntu partition after losing a couple years to Warcraft...)

---

### Post by alexeix on 2009-03-15
Thanks for the replies. 

lisati:
I'm looking for a free solution (should have specified that), so don't want to pay for Nero (but thanks for the suggestion!).

flugh:

I don't understand that method.  What does it actually do?  I don't think my installation disk contains an image.


Can I just copy all the files off the disk and then burn an image from the resulting files?

---

### Post by lisati on 2009-03-15
> **alexeix said:**
> Thanks for the replies. 

lisati:
I'm looking for a free solution (should have specified that), so don't want to pay for Nero (but thanks for the suggestion!).

flugh:

I don't understand that method.  What does it actually do?  I don't think my installation disk contains an image.


Can I just copy all the files off the disk and then burn an image from the resulting files?

flugh's method is from the command line.....

---

### Post by alexeix on 2009-03-15
I recognise it as a command line instruction, but not what it's doing, which means I don't know how to apply it on my installation.

Can you break it down and give an accurate example, so I can interpret it please?

Is 'mybackup.iso' the suggested output name of the files copied from the DVD?

---

### Post by alexeix on 2009-03-15
Okay, so I installed Nero, but I still don't see how to get the data off the disk.  My PC only has one DVD drive, so I need to extract the data first.
Does this need to be done using particular software?

---

### Post by mb_webguy on 2009-03-15
The dd command copies raw information from a drive.  The "if" option defines the input file (usually a device), and the "of" option defines the output file.  This can be another device, which effectively clones a drive.   In this case, the input is a cd and the output is an iso file, thus making a disc image.

k3b and (I believe) Brasero can copy a disc to an image rather than to another disc.

---

