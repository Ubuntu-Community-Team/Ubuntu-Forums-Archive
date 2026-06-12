---
title: "Ubuntu fails to boot - (usually)"
date: 2008-12-13
forum: General Help
---

### Post by razorbak on 2008-12-13
Hi

I have installed UBUNTU 8.10.
I used the supplied partioner...creating a single partion for Ubuntu.
My problem is that Ubuntu fails to boot most times but strangely sometimes works.
Please help!

---

### Post by hikaricore on 2008-12-13
Without any error messages or anything else to gdo on, no one will be able to assist you.

Please provide more info about your troubles.

---

### Post by razorbak on 2008-12-13
message : "No operating system found"

But as I say soetimesboots fine

---

### Post by razorbak on 2008-12-13
I put the bootloader on HD0.  When the systems does a sucesfull boot I notice grub booting from HD0,0.
Did I put the loader in the right place?

---

### Post by hikaricore on 2008-12-13
I've had this issue with an older PC which I expect is related to a subpar motherboard/bios.

Your grub is likely in the correct place so I doubt that's an issue.
You may want to check your bios setting for an option such as Boot Delay.

On the troubled system I mentioned setting a boot or drive delay of 10 seconds or so made similar issues go away as the drive has time to fully power up and can be recognized by the system before attempting to load the OS.

To sum it all up I'm thinking this is more a hardware issue than a Linux issue in general, but that's just my opinion.  Hope this is somewhat helpful.

---

### Post by razorbak on 2008-12-13
The machine is a Samsung Q310 laptop (2 months old).  Many Thanks I will give that a try.

---

### Post by razorbak on 2008-12-13
No delay optionis available in the BIOS.  All very disapointing.

---

### Post by razorbak on 2008-12-13
disabled HDC1 in Bios and seems fine now

---

### Post by Dwiman89 on 2008-12-16
IM having the same issue. I dont have a HDC1 option in the BIOS nor a time limit option...

---

