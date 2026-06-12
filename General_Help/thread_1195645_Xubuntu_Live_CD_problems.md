---
title: "Xubuntu Live CD problems"
date: 2009-06-24
forum: General Help
---

### Post by nboy56 on 2009-06-24
I have a Micron Transport Trek 2 with 256MB RAM 20GB HDD and an Intel Inside Pentium 2 processor so I thought Xubuntu 9.04 would be perfect and I downloaded live CD burned it and it acted like it was working but then there was always some idiotic error or something I had previously installed ubuntu 8.10 but there was so many glitches and it was way way way toooo slow so i opted for xubuntu should i use the alternate CD instead??? I really need help

---

### Post by merlinus on 2009-06-24
You might try the alternate install cd, but first do a checksum to ensure your .iso is not corrupted, and burn it at no more than 4x speed.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by nboy56 on 2009-06-24
Ok that might have been it i burned it a 10X speed so ill bring it down to 4X and see if that works

---

### Post by snowpine on 2009-06-24
> **nboy56 said:**
> it acted like it was working but then there was always some idiotic error or something

The errors may seem "idiotic" to you, but they would be very helpful to someone trying to help you. :) Post more specifics about your problem and I'm sure you'll get some helpful advice.

---

### Post by nboy56 on 2009-06-27
Im sorry it would say "APCI BIOS age fails cutoff acpi=force is required" 
then it would say  
"APIC resources failed to load 
Loading please wait" 
then the xubuntu loading screen would show up and the bar would bounce back and forth like usual but when the bar started to progress it stalled at the [x] in xubuntu and gave me an error messsage

---

### Post by QIII on 2009-06-27
I wouldn't worry about the "APCI BIOS age fails cutoff acpi=force is required".  That's a consequence of having older hardware and the associated BIOS.  It just means that acpi will be forced.

The other message is intriguing, since it seems APCI can't be loaded.  I'll do some research on that.

What is the final error you are getting?  "an error" is not really descriptive enough.

And, yes, the alternate install MAY work better.  But let's see if we can resolve this issue anyway.

---

### Post by snowpine on 2009-06-27
At the first screen, you can press one of the Fn keys for boot options (sorry I forget which one). Try adding 'acpi=force' or 'noacpi' (without the quotes) to the end of this line, that might do the trick.

---

