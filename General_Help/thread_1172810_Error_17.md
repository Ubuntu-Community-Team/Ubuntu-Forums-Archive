---
title: "Error 17?"
date: 2009-05-29
forum: General Help
---

### Post by princessdoom13 on 2009-05-29
Greetings friends,
Alas, I have encountered great grief when I turned on my HP dv9700 laptop... The load screen stated:
[B]GRUB Loading stage1.5.

GRUB Loading, please wait...
Error 17[/B]
_

I have NO idea why this is happening and I also have NO idea what to do, considering that 
1.) My computer normally, upon boot-up, comes to a screen that gives me the option of booting into either Ubuntu or Vista
2.) My CD/DVD drive is broken/burned out, and therefore I can't even run off of a live CD (in addition to my previously already having trouble with connecting to WiFi in Ubuntu)
and
3.) I do photography/writing on the side, and I would really love to have my files back...

So, in conclusion, someone _***PLEASE***_ help end my current stroke of technological bad luck and say that there is SOMETHING I can do... ANY help is greatly appreciated!

Thanks bunches, friends.
-S
***
PS, additional information: I have Ubuntu version 7.10, as well as Windows Vista 64 Bit...

---

### Post by VMC on 2009-05-29
"17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the file system type cannot be recognised by GRUB."

So the question is what were you doing just before this happened?

Your going to need some way to get linux running. Can you get to the grub prompt from that error message. Type 'c' and see if you get to the "grub>"  prompt.

---

### Post by 101011010010 on 2009-05-29
*I don't know if this will help, but I recently got an Error 17. I did a clean install of Vista 64 on one hard drive and Ubuntu 64 on the other. I forgot that grub is installed over the Vista MBR and so I had to make the Vista hard drive boot first in the Bios. I hope this helps.*

---

